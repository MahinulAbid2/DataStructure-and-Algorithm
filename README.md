# Creating HashTable in JavaScript
```javascript
class Hashkey {
    constructor(size) {
        this.data = new Array (size);
    }

    _hashKey ( key ) {
        let hash = 0;
        for ( let i = 0; i < key.length; i++) {
            hash = ( hash + key.charCodeAt (i) * i) % this.data.length;

        }

        return hash;
    }


    insertData (key, value) {
        let hashedKey = this._hashKey(key);

        // hash key gives a random number that stays between array size
        // I can use that hashkey as index number to store the data
        // 
        if(this.data[hashedKey] === undefined){
            this.data[hashedKey] = []; // set up an empty array
        }
        this.data[hashedKey].push([hashedKey,value]);
    
    }

    getValue (key) {
        let HashedKey = this._hashKey(key);
        let value = this.data[HashedKey];
        return value;
    }

    getIndividualValue (key) {
        let HashedKey = this._hashKey(key);
        let Arr = this.data[HashedKey];
        let ReturnValue = [];

        for ( let i = 0; i < Arr.length; i++ ) {
            // loop through the array and 
            // return an array containing just the value
            if(Arr.length > 1){
                
                ReturnValue.push(Arr[i][1]);
            }

            else {
                ReturnValue = Arr[0][1];
            }
        }

        return ReturnValue;
    }
}


let hashedData = new Hashkey(20); // created new hashtable

hashedData.insertData("firstname" , "john");

hashedData.insertData("firstname" , "kate");



console.log ( hashedData.getIndividualValue("firstname") );
```

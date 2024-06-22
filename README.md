## Flattening Object using different looping methods Methods

### `getFlatObject` Function Implementations

#### Method 1: Using `Object.entries` and `forEach`

```javascript
/**
 * Recursively flattens an object into a single-level object.
 * Uses Object.entries and forEach for iteration.
 *
 * @param {Object} obj - The object to flatten.
 * @param {string} [prefix=''] - The prefix for flattened keys.
 * @returns {Object} - The flattened object.
 */
const getFlatObject = (obj, prefix = '') => {
    let x = {};
    Object.entries(obj).forEach(([key, val]) => {
        if (typeof val === 'object') {
            const nestedObject = getFlatObject(val, `${key}.`);
            x = {...x, ...nestedObject};
        } else {
            x[`${prefix}${key}`] = val;
        }
    });
    return x;
};
const getFlatObject=(obj,prefix='')=>{
    let x={}
  Object.entries(obj).forEach(([key,val])=>{
    if(typeof val==='object') {
    const nestedobject =getFlatObject(val,`${key}.`)
    x={...x,...nestedobject}
    }
    else {
        x[`${prefix}${key}`]=val
    }
  })
 return x
}

const getFlatObject=(obj,prefix='')=>{
    let x={}
  for(const i in obj) {
      if(typeof obj[i] ==='object') {
          const nestedObject=getFlatObject(obj[i],`${prefix}${i}.`)
          x={...x,...nestedObject}
      }
      else {
          x[`${prefix}${i}`]=obj[i]
      }
  }
 return x
}

const getFlatObject=(obj,prefix='')=>{
    let x={}
  for(const [key,value] of Object.entries(obj)) {
      if(typeof value ==='object') {
          const nestedObject=getFlatObject(value,`${prefix}${key}.`)
          x={...x,...nestedObject}
      }
      else {
          x[`${prefix}${key}`]=value
      }
  }
 return x
}
const  flattenObject=(obj, prefix = '')=> {
   return Object.keys(obj).reduce((acc,key)=>{
       if(typeof obj[key]=='object') {
         Object.assign(acc,flattenObject(obj[key],prefix+key+'.'))
       }
       else {
           acc[prefix+key]=obj[key]
       }
       return acc;
   },{})
}

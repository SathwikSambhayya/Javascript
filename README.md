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

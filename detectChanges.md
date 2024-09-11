To determine the changes between `v1` and `v2` and produce the desired output JSON based on the type of change (key removed, key added, or value modified), you can use a function to compare the two objects and output the results according to your rules. Here's how you can do it:

```javascript
function detectChanges(v1, v2) {
    const result = {};

    function compareObjects(obj1, obj2) {
        const keys1 = Object.keys(obj1);
        const keys2 = Object.keys(obj2);

        // Check for removed or modified keys
        keys1.forEach(key => {
            if (!keys2.includes(key)) {
                // Key is removed in v2
                result[key] = 1;
            } else if (JSON.stringify(obj1[key]) !== JSON.stringify(obj2[key])) {
                // Key is modified in v2
                result[key] = 3;
            }
        });

        // Check for added keys
        keys2.forEach(key => {
            if (!keys1.includes(key)) {
                // Key is added in v2
                result[key] = 2;
            }
        });
    }

    compareObjects(v1, v2);
    return result;
}

const v1 = { a: { name: "tea", price: 20 }, b: { name: "car", price: 13, info: { sku: 123, tag: ["trend"] } } };
const v2 = { b: { name: "car", price: 13, info: { sku: 123, tag: ["trend", "top"] } }, c: { name: "fan", price: 55 } };

const changes = detectChanges(v1, v2);
console.log(changes);  // Output: { a: 1, c: 2, b: 3 }
```
# importtant !
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    <script>
    
    
        console.log(JSON.stringify({a:1,b:2,}) == JSON.stringify({a:1,b:2})); // true
        console.log(JSON.stringify({b:2,a:1}) == JSON.stringify({a:1,b:2})); // false
    
    
        // Assign Lodash to a variable named `lodash`
        const lodash = _;

        // Now use lodash.isEqual
        const object1 = { 'a': 1, 'b': {a1:5,b1:5} };
        const object2 = { 'a': 1, 'b': {b1:5,a1:5}};
        
        console.log(lodash.isEqual(object1, object2)); // true
    </script>
</body>
</html>

```


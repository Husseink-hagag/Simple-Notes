##new

##
```javascript
function jsonToStringUrl(jsonParam) {
    const stringUrlList = [];

    for (let key in jsonParam) {
        stringUrlList.push(`${key}-${jsonParam[key]}`);
    }

    return stringUrlList.join('/');
}

// Example usage
const jsonParam = {
    "pgNum": 1,
    "tag": "cloth",
    "sortby": "new"
};

const stringUrl = jsonToStringUrl(jsonParam);
console.log(stringUrl); // Output: pgNum-1/tag-cloth/sortby-new

```

##
```javascript
function stringUrlToJson(stringUrl) {
    const keys_values = stringUrl.split('/');
    const jsonResult = {};

    for (let key_value of keys_values) {
        [key, value] = key_value.split('-');
        jsonResult[key] = value;
    }

    return jsonResult;
}

const stringUrl = 'pgNum-1/tag-cloth/sortby-new';
const jsonResult = stringUrlToJson(stringUrl);
console.log(jsonResult); // Output: { pgNum: '1', tag: 'cloth', sortby: 'new' }

```



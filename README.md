# SDET Technical Assesment - Nomor 1

Automation test dijalankan menggunakan Postman.

Link API : https://jsonplaceholder.typicode.com/posts


## GET All Data

```javascript
pm.test('status code should be 200', () => {
    pm.response.to.have.status(200);
});

pm.test('response header Content-Type should be application/json', () => {
    pm.expect(pm.response.headers.get('Content-Type')).to.equals('application/json; charset=utf-8');
});

pm.test('response body should be an object', () => {
    const responseJson = pm.response.json();
    pm.expect(responseJson).to.be.an('array');
});

pm.test('response body object should have correct property', () => {
    const responseJson = pm.response.json();

    _.each(responseJson, (property) => {
        pm.expect(property).to.haveOwnProperty('userId');
        pm.expect(property).to.haveOwnProperty('id');
        pm.expect(property).to.haveOwnProperty('title');
        pm.expect(property).to.haveOwnProperty('body');

        pm.expect(property.userId).to.be.a('number');
        pm.expect(property.id).to.be.a('number');
        pm.expect(property.title).to.be.a('string');
        pm.expect(property.body).to.be.a('string');
    })
});
```

## POST Data

```javascript
pm.test('status code should be 201', () => {
    pm.response.to.have.status(201);
});

pm.test('response header Content-Type should be application/json', () => {
    pm.expect(pm.response.headers.get('Content-Type')).to.equals('application/json; charset=utf-8');
});

pm.test('response body should be an object', () => {
    const responseJson = pm.response.json();
    pm.expect(responseJson).to.be.an('object');
});

pm.test('response body should have correct property and value', () => {
    const responseJson = pm.response.json();
    
    pm.expect(responseJson).to.haveOwnProperty('title');
    pm.expect(responseJson).to.haveOwnProperty('body');
    pm.expect(responseJson).to.haveOwnProperty('userId');

    pm.expect(responseJson.title).to.equals('recommendation');
    pm.expect(responseJson.body).to.equals('motorcycle');
    pm.expect(responseJson.userId).to.equals(6)
});
```

# SDET Technical Assesment - Nomor 2

[Nomor 2](https://github.com/hafezdeldaffa/sdet-test/tree/master/nomor2)

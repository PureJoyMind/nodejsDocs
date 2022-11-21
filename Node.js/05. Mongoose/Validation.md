# Validation In Schema

we can pass an object in our schema definition instead of the type of that key. This object is:
`{ type: dataType, required: true }`. This will make mongoose check the object before creating a document in the database. If the key with the required set to true is missing mongoose will throw an exception.
So when creating an object and using the `save()` method we need to use a `try` and `catch` block to catch exceptions.

```js
async function createCourse(){
    const course = new Course({
        name: 'practice',
        author: 'Maz',
        tags: ['course', 'backend'],
        published: true,
        price: 15
    });

    try{
        const result = await course.save();
        console.log('result:\n', result);
    }catch(ex){
        console.log(ex.message);
    }
}
```

`required` is a built-in validator in mongoose.

## Built-in Validators

When using the `required` validator, we can either use a boolean or a function that returns a boolean. So we can have conditions in our schema definitions:

```json
{
	published: Boolean,
	price: {
		type: Number,
		required: function(){ return(this.published) }
	}
}	
```

This code is a part of our schema definition. It means that the price key is only needed if we have the published set to true.

***Note***: we cannot use the `=>` operator here because the arrow operator does not have `this`. They do but it works in a function call. So if we use the arrow function here, the `this` refers to the function instance that is going to call the schema. Which will not happen.

Depending on the type of our property we have additional built-in validators. For example for Strings we have the following validators:

```json
{
type: String,
required: true,
minLength: 5,
maxLength: 255,
match: /regularExpression/,
enum: ['s1', 's2', 's3']
}
```

The `enum` validator recieves an array, and our string can only be one of the strings in the array.

Also Numbers have the `min` and `max` validators. 
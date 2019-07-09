# AWS Serverless APIs & Apps

https://www.udemy.com/aws-serverless-a-complete-introduction


## Body Mapping Templates can be confusing, but in the end, they're not that difficult. 

You use the Apache Velocity Language when working with these templates, that will only matter once you create more complex transformations though. Basic explanations (see below) should be relatively self-explanatory

First, you need to understand that they simply allow you to control which data your action receives (e.g. Lambda).

You can for example transform incoming data of the following shape:

```
{
    person: {
        name: "Max",
        age: 28
    },
    order: {
        id: "6asdf821ssa"
    }
}
```

to 

```
{
    personName: "Max",
    orderId: "6asdf821ssa"
}
```

with the following template:

```
{
    "personName": "$input.json('$.person.name')",
    "orderId": "$input.json('$.order.id')"
}
```

$input  is a reserved variable, provided by AWS which gives you access to the input payload (request body, params, headers) of your request.

Link: http://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-mapping-template-reference.html#input-variable-reference

json()  is a method on $input  which will retrieve a JSON representation of the data you access. $  here stands for the request body as a whole, $.person.name  therefore accesses the name property on the person property which is part of the whole requests body object.

The $input.json(...)  code is wrapped into quotation marks (" ) because it should be transformed into a string in this example (since both name and id are strings). If you were to access a number, boolean or object here, you would NOT wrap the expression in quotation marks.

Example - Accessing a Number:

```
{
    "extractedAge": $input.json('$.person.age')
}
```

You can learn more about the reserved variables provided by AWS and the different utility functions it offers here: http://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-mapping-template-reference.html


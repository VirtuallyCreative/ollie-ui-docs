---
title: Mock API Data Schema
weight: 6
template: docs
---

Ollie-UI uses a three step process to create a mock API.

First is declaring the schema for our mock API using [JSON Schema Faker](https://json-schema-faker.js.org/), this will allow us to declare exactly what our fake API should look like, we'll declare the objects and properties that it will expose including the data types.

Step two involves generating random data, [JSON Schema Faker](/Mock-API-Data-Schema) supports generating random data using a few open source libraries, `faker.js`, `chance.js` and `randexp.js`. Faker and Chance are very similar, both of these libraries offer a wide variety of functions for generating random data including realistic names, address, phone numbers, emails and much more. Randexp focuses on creating random data based on regular expressions. Now JSON Schema Faker allows us to use Faker, Chance and Randexp with our schema definitions!

So we'll declare exactly how each property in our mock API should be generated, this will ultimately produce a big chunk of JSON, and the nice thing is, that big chunk of JSON will contain different data every time that we run JSON Schema Faker, and that's where our final piece comes in.

In the example below, we make one object (`users`) that returns randomized data for each key-value pair.

```json
export const schema = {
  "type": "object",
  "properties": {
    "users": {
      "type": "array",
      "minItems": 3,
      "maxItems": 5,
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "type": "number",
            "unique": true,
            "minimum": 1
          },
          "firstName": {
            "type": "string",
            "faker": "name.findName"
          },
          "lastName": {
            "type": "string",
            "faker": "name.lastName"
          },
          "email": {
            "type": "string",
            "faker": "internet.email"
          }
        },
        "required": ["id", "firstName", "lastName", "email"]
      }
    }
  },
  "required": ['users']
};
```

JSON Schema is a standard for describing a JSON data format. Of course, since JavaScript is the Wild West, this is just one of many so called standards for describing JSON structures, there's also JSON Content Rules, JSON LD, RAML and API related technologies like GraphQL, Falcor and O Data that specify their own standards for JSON structures.

This is the standard that we'll be following to declare the shape of our mock data, and here's why, JSON Schema Faker is a handy tool that uses the JSON Schema standard. And enhances it by using some open source libraries for generating mock data.

As mentioned, the three libraries that we'll be using are `Faker.js`, `Chance.js` and `Randexp.js`, all three of these libraries come bundled with JSON Schema Faker. As you can see above, Ollie-UI is using Faker to generate email address, names and random URLs.

Also, be sure to check out the [JSON Schema Faker repl](https://json-schema-faker.js.org/) online this way you can easily try different schemas and instantly what JSON they produce. I found this to be a great way to rapidly learn how to structure my schema.

Now the biggest caveat with using this tool is it has strong opinions on what a FAKE REST API should look like. If an existing API that has dramatically different assumptions than this makes, then this won't be very helpful, but if you haven't built your service yet or your service follows the same popular conventions as this library, then JSON server can help you stand up a mock API shockingly quickly.

[JSON server](https://www.npmjs.com/package/json-server) creates a realistic API using a static JSON file behind the scenes, so Ollie-UI points JSON Server at the mock data set that is dynamically generated. The beauty of JSON Server is it actually supports create, reads, updates and deletes, so it saves changes to the JSON file that's being created by JSON Schema Faker!

This way, the API feels just like a real API but without having to make an actual over-the-network HTTP call or needing to stand up a real database. This means that to get started on development, we just need to agree on the calls that we want to make and the data shape that those calls should return. Then the UI team can move ahead without having to wait on a service team to actually create those associated services, everyone can code to an interface and get back together later.
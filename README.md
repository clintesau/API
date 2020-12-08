![David](https://img.shields.io/david/clintesau/API)
![GitHub](https://img.shields.io/github/license/clintesau/API)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/clintesau/API)
![GitHub deployments](https://img.shields.io/github/deployments/clintesau/API/clintesau-api)
[![Heroku App Status](http://heroku-shields.herokuapp.com/clintesau-api)](https://clintesau-api.herokuapp.com)

<div align="center"><h1><a href="https://api.clintesau.me" title="REST API">Strapi REST API</a></h1></div>

<p align="center">
  <img alt="Strapi Headless CMS" src="https://ce-projects.s3-ap-southeast-2.amazonaws.com/github_main_c889384d9e.PNG">
</p>

<div align="center"><p><strong>REST API</strong> for managing my Personal Projects data that I will be using to request data needed for my <a href="https://clintesau.me" title="Portfolio">Portfolio website</a> to keep the Projects section dynamic. As I add, update and remove projects over time the api will update the <a href="https://clintesau.me" title="Portfolio">Portfolio website</a> with all the relevant up-to-date data. Showing only what I want without me having to touch the <a href="https://clintesau.me" title="Portfolio">Portfolio website</a> code and only manage it with <a href="https://clintesau.me" title="Strapi">Strapi's Headless CMS</a> easily and fast. <img width="15" alt="Thumbs Up" src="https://github.githubassets.com/images/icons/emoji/unicode/1f44d.png?v8"></p></div>

## [Strapi](https://strapi.io/) Installation from CLI

```shell
  npx create-strapi-app my-project --quickstart
```

> **ProTip:** If you want to use specific database, you don't have to use the --quickstart flag. The CLI will let you choose the database of your choice if you use the following command.

```shell
  npx create-strapi-app my-project
```

I chose to use **MongoDB** as the database client and used [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) as the cloud database for **MongoDB**.

## REST API Access

You can publish your file by opening the **Publish** sub-menu and by clicking **Publish to**. For some locations, you can choose between the following formats:

### Endpoints (Public Access)

Endpoints for viewing the Projects that the Public User
has permissions to access.

* [Show Accessible Projects](https://api.clintesau.me/projects) : `GET /projects/`
* [Show A Project](https://api.clintesau.me/projects/5fce9b9f0ee7276bec897035/) : `GET /projects/{id}/`
* [Show Projects Count](https://api.clintesau.me/projects/count/) : `GET /projects/count/`

Another really handy feature from **Strapi** is the ability to add query parameters to certain requests to filter the data in any way you want. I'll add a couple of endpoints below.

* [Show Accessible Projects with a limit](https://api.clintesau.me/projects?_limit=2) : `GET /projects?_limit=2`
* [Show Accessible Projects sorted according to a specific field](https://api.clintesau.me/projects?_sort=title) : `GET /projects?_sort=title`
* [Show Accessible Projects that are featured](https://api.clintesau.me/projects?is_featured=true) : `GET /projects?is_featured=true`

### Endpoints (Authorization Required)

Endpoints for manipulating the Projects that only the Authenticated User
has permissions to access.

* Create Project : `POST /projects/`
* Update A Project : `PUT /projects/{id}/`
* Delete A Project : `DELETE /projects/{id}/`

### Documentation Plugin

This plugin generates the **API** documentation for you using [Swagger UI](https://swagger.io/tools/swagger-ui/). You'll be able to visualize all your end-points directly from the [Swagger UI](https://swagger.io/tools/swagger-ui/). 

Once your **Strapi** application is built, install the **Documentation Plugin** from the Admin Plugins panel.

[Swagger UI docs](https://api.clintesau.me/documentation/v1.0.0#/)

## AWS S3 Provider

### Installation

```shell
  npm i strapi-provider-upload-aws-s3
```

### Configuration

```shell
  ./config/plugins.js
```

```js
module.exports = ({ env }) => ({
  // ...
  upload: {
    provider: 'aws-s3',
    providerOptions: {
      accessKeyId: env('AWS_ACCESS_KEY_ID'),
      secretAccessKey: env('AWS_ACCESS_SECRET'),
      region: env('AWS_REGION'),
      params: {
        Bucket: env('AWS_BUCKET'),
      },
    },
  },
  // ...
})
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

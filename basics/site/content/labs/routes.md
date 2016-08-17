---
date: 2016-04-19T19:21:15-06:00
title: Routes
---

In this exercise, you will use a blue-green deployment to perform an update to your app.


## Create a new route

First, you will want to create a route whereby your application will be accessible.  Since this route will remain as the app evolves, we will create it manually instead of when pushing the first version of our app.

* Use `cf create-route` to a create a new route for your app.

### Push v1.0

* First, deploy the app from **TO DO**.
* Use `cf help` to figure out how to map your route above to this app.  
* Verify your app is accessible by accessing the route you created.
* Change to the `08-domains-routes/v1.0` directory and push the v1.0 app.

#### Checking Your Work

You should be able to access your app on the route created above.  You should also be able to see the route/url by looking at the app details:

```sh
cf app
```

### Push v1.1

* Now, deploy version 1.1 of the app from **TO DO**.  Do not map your main route yet.  You want the app to be validated before directing traffic to it.
* Validate you can access the app by accessing the automatically assigned route.
* Now use the CF cli to map traffic to v1.1.  You should have some traffic going to v1.0 and some to v1.1.
* Change to the `08-domains-routes/v1.1` directory and push the v1.0 app.

#### Checking Your Work

Check your work by accessing the main route multiple times.  You should observe traffic being balanced across both instances.  You can also see the routes/urls by looking at the app details:

```sh
cf app
```

### Cutting over  

* Use `cf help` to figure out how to stop sending traffic to v1.0.

#### Checking Your Work

Check your work by accessing the main route multiple times.  You should observe traffic only going to v1.1.  You can also see the routes/urls by looking at the app details:

```sh
cf app
```

Congratulations!  You successfully updated your running application to a new version with no user interruption.


## Beyond the Class

  * Set up a custom [SSL certificate](http://www.selfsignedcertificate.com/)
  * Use [feature flags](https://docs.cloudfoundry.org/adminguide/listing-feature-flags.html) instead of ENV vars
  * Delete all routes that are no longer used

```bash
$ cf delete-orphaned-routes
```
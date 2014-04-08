SendGrid
=======

[SendGrid][sendgrid-addon] is an [add-on][modulus-addon] for providing scalable email delivery and analytics for apps.

SendGrid's cloud-based email infrastructure relieves businesses of the cost and complexity of maintaining custom email systems. SendGrid provides reliable delivery, scalability and real-time analytics along with flexible APIs that make custom integration a breeze.

## Provisioning the add-on

SendGrid can be attached to a Modulus application via the  CLI:

    $ modulus addons add sendgrid:free
or from the [web interface][sendgrid-addon]  

A list of all plans available can be found [here][sendgrid-addon].

Once SendGrid has been added `SENDGRID_USERNAME`, `SENDGRID_PASSWORD` settings will be available in the app configuration and will contain the credentials used to access the newly provisioned SendGrid service instance. This can be confirmed using the `modulus env get` command.

    $ modulus env get SENDGRID_USERNAME
    sendgrid100099@modulus.io

    $ modulus env get SENDGRID_PASSWORD
    password

After installing SendGrid the application should be configured to fully integrate with the add-on.


## Node.js

SendGrid has a Node.js package that is written and maintained by two
core engineers. The code is open source and available on [Github](http://github.com/sendgrid/sendgrid-nodejs).

Add the following settings in package.json file

#### package.json
-----------------

    {
      "name": "node-sendgrid-example",
      "version": "0.0.1",
      "dependencies": {
        "express": "3.x",
        "sendgrid": "1.0.2"
      }
    }

Install SendGrid locally with the following command:
`npm install`

#### program.js
-----------------
To begin using this library, initialize the sendgrid object with your SendGrid credentials:

    var sendgrid  = require('sendgrid')(
      process.env.SENDGRID_USERNAME,
      process.env.SENDGRID_PASSWORD
    );

Send the email.

    sendgrid.send({
      to: 'example@example.com',
      from: 'sender@example.com',
      subject: 'Hello World',
      text: 'Sending email with NodeJS through SendGrid!'
    }, function(err, json) {
    if (err) { return console.error(err); }
      console.log(json);
    });

Full documentation of all the features of SendGrid's Node.js package can
be found on [Github](http://github.com/sendgrid/sendgrid-nodejs)


## Dashboard

SendGrid offers statistics a number of different metrics to report on what is happening with your messages.
![ScreenShot](https://sendgrid.com/docs/images/delivery_metrics.png)

The dashboard can be accessed visiting the [Modulus dashboard][modulous-dashboard] and selecting the project in question. Select SendGrid from the Add-ons menu.


## Migrating between plans

Plan migrations are easy and instant. Use the [Modulus dashboard][modulous-dashboard] to migrate to a new plan.


## Removing the add-on

SendGrid can be removed from the [dashboard][modulous-dashboard]. If you accidentally remove the SendGrid add-on, re-adding SendGrid will resume your access to the account


## Support

One of SendGrid's best features is its responsive customer service. You can contact SendGrid 24/7 by phone, web, and live chat:

* [http://support.sendgrid.com](http://support.sendgrid.com/)
* Toll Free: +1 (877) 969-8647
* [support@sendgrid.com](mailto:support@sendgrid.com)


## Additional resources

Additional resources are available at:

- [Integrate With SendGrid](http://sendgrid.com/docs/Integrate/index.html)
- [Code Examples](http://sendgrid.com/docs/Code_Examples/index.html)


[sendgrid-addon]: https://addons.modulus.io/sendgrid
[modulus-addon]: https://addons.modulus.io/
[modulous-dashboard]: https://modulus.io/user/dashboard

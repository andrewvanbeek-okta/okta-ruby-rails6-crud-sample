# Rails 6 sample

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

**Prerequisites:** 
- [Rails 6](https://guides.rubyonrails.org/)+


Clone this application to your local hard drive using Git.

```
git clone https://github.com/oktadeveloper/okta-ruby-rails6-crud-sample.git
```

Install this example's dependencies, create the database, and run the migrations, also add webpacker just in case there are inconsitencies in your enviroment:

```
bundle install
bundle exec figaro install
yarn add @rails/webpacker
```

Before going futher make sure you add a placeholder in your config/application.yml


```
OKTA_CLIENT_ID: "okta client id"

OKTA_CLIENT_SECRET: "okta client secret"

OKTA_ORG: "dev-1234" // your org so this is usually something like dev-{some random number or guid} or the name of your company like acme, it is usally right before your domain of okta or okta or oktapreview
OKTA_DOMAIN: "okta" //your org so this usually something like dev-{some random number or guid} or the name of your company like, it is usally right before your domain of okta or okta or oktapreview

OKTA_URL: "your okta url"

OKTA_ISSUER: "your okta oauth server issuer" // go to API > Authorization Servers to find your Issuer

OKTA_AUTH_SERVER_ID: "default" //typically default unless you created a custom oauth server, then it is the id after /oauth2/ in your issuer

OKTA_REDIRECT_URI: "http://localhost:3000/users/auth/oktaoauth/callback"
```

Install this example's dependencies, create the database, and run the migrations:
```
rake db:create
rake db:migrate
```

### Use Okta for Identity

You will need to create an OIDC Application in Okta to get your configuration settings to log in. You'll need to create an Okta developer account and register your app to get a client ID. Head on over to [developer.okta.com/signup](https://developer.okta.com/signup) if you'd like to do this in your browser. 

On the Create New Application page, select **Web**. Name your app `Ionic Social`, and configure it as follows:

* Base Uri:
  *`http://localhost:3000`
* Login redirect URIs: 
  * `http://localhost:3000/users/auth/oktaoauth/callback`
* Grant type allowed: 
  - [x] **Authorization Code**
* Click **Done**

For the extra Crud steps follow the blog to add a custom attribute of "gemstone", [help link](https://help.okta.com/en/prod/Content/Topics/users-groups-profiles/usgp-add-custom-attributes.htm) .

Now go back to your rails application and modify your application.yml file.

```
OKTA_CLIENT_ID: "okta client id"

OKTA_CLIENT_SECRET: "okta client secret"

OKTA_ORG: "dev-1234" // your org so this is usually something like dev-{some random number or guid} or the name of your company like acme, it is usally right before your domain of okta or okta or oktapreview
OKTA_DOMAIN: "okta" //your org so this usually something like dev-{some random number or guid} or the name of your company like, it is usally right before your domain of okta or okta or oktapreview

OKTA_URL: "your okta url"

OKTA_ISSUER: "your okta oauth server issuer" // go to API > Authorization Servers to find your Issuer

OKTA_AUTH_SERVER_ID: "default" //typically default unless you created a custom oauth server, then it is the id after /oauth2/ in your issuer

OKTA_REDIRECT_URI: "http://localhost:3000/users/auth/oktaoauth/callback"
```

Run `rails s` and open `http://localhost:3000` in a new incognito window. Click **Sign in with Okta** to sign in to your Okta developer account.

## Links

This example uses the following open source libraries:

* [Omniauth](https://github.com/omniauth/omniauth)
* [Devise](https://github.com/heartcombo/devise)
* [omniauth-rails_csrf_protection](https://github.com/omniauth/omniauth/wiki/Resolving-CVE-2015-9284)

This sample also uses a generic Okta omniauth Strategy, but it is not a official Okta rails SDK

* [https://github.com/andrewvanbeek-okta/omniauth-oktaoauth](https://github.com/andrewvanbeek-okta/omniauth-oktaoauth)

## Help

Please post any questions as issues in this forum, as questions on the [blog post](https://developer.okta.com/blog/2020/09/21/ionic-apple-google-signin), or on [Stack Overflow](https://www.stackoverflow.com) with an "okta" tag.

## License

Apache 2.0, see [LICENSE](LICENSE).

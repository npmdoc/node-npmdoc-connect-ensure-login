# api documentation for  [connect-ensure-login (v0.1.1)](https://github.com/jaredhanson/connect-ensure-login#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-connect-ensure-login.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-connect-ensure-login) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-connect-ensure-login.svg)](https://travis-ci.org/npmdoc/node-npmdoc-connect-ensure-login)
#### Login session ensuring middleware for Connect.

[![NPM](https://nodei.co/npm/connect-ensure-login.png?downloads=true)](https://www.npmjs.com/package/connect-ensure-login)

[![apidoc](https://npmdoc.github.io/node-npmdoc-connect-ensure-login/build/screenCapture.buildNpmdoc.browser.%2Fhome%2Ftravis%2Fbuild%2Fnpmdoc%2Fnode-npmdoc-connect-ensure-login%2Ftmp%2Fbuild%2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-connect-ensure-login/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-connect-ensure-login/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-connect-ensure-login/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jared Hanson",
        "email": "jaredhanson@gmail.com",
        "url": "http://www.jaredhanson.net/"
    },
    "bugs": {
        "url": "http://github.com/jaredhanson/connect-ensure-login/issues"
    },
    "dependencies": {},
    "description": "Login session ensuring middleware for Connect.",
    "devDependencies": {
        "vows": "0.6.x"
    },
    "directories": {},
    "dist": {
        "shasum": "174dcc51243b9eac23f8d98215aeb6694e2e8a12",
        "tarball": "https://registry.npmjs.org/connect-ensure-login/-/connect-ensure-login-0.1.1.tgz"
    },
    "engines": {
        "node": ">= 0.4.0"
    },
    "homepage": "https://github.com/jaredhanson/connect-ensure-login#readme",
    "keywords": [
        "connect",
        "express",
        "auth",
        "authn",
        "authentication",
        "login",
        "session",
        "passport"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://www.opensource.org/licenses/MIT"
        }
    ],
    "main": "./lib",
    "maintainers": [
        {
            "name": "jaredhanson",
            "email": "jaredhanson@gmail.com"
        }
    ],
    "name": "connect-ensure-login",
    "optionalDependencies": {},
    "readme": "# connect-ensure-login\n\nThis middleware ensures that a user is logged in.  If a request is received that\nis unauthenticated, the request will be redirected to a login page.  The URL\nwill be saved in the session, so the user can be conveniently returned to the\npage that was originally requested.\n\n## Install\n\n    $ npm install connect-ensure-login\n\n## Usage\n\n#### Ensure Authentication\n\nIn this example, an application has a settings page where preferences can be\nconfigured.  A user must be logged in before accessing this page.\n\n    app.get('/settings',\n      ensureLoggedIn('/login'),\n      function(req, res) {\n        res.render('settings', { user: req.user });\n      });\n      \nIf a user is not logged in when attempting to access this page, the request will\nbe redirected to '/login' and the original request URL ('/settings') will be\nsaved to the session at 'req.session.returnTo'.\n\n#### Log In and Return To\n\nThis middleware integrates seamlessly with [Passport](http://passportjs.org/).\nSimply mount Passport's 'authenticate()' middleware at the login route.\n\n    app.get('/login', function(req, res) {\n      res.render('login');\n    });\n\n    app.post('/login', passport.authenticate('local', { successReturnToOrRedirect: '/', failureRedirect: '/login' }));\n    \nUpon log in, Passport will notice the 'returnTo' URL saved in the session and\nredirect the user back to '/settings'.\n\n#### Step By Step\n\nIf the user is not logged in, the sequence of requests and responses that take\nplace during this process can be confusing.  Here is a step-by-step overview of\nwhat happens:\n\n1. User navigates to 'GET /settings'\n    - Middleware sets 'session.returnTo' to '/settings'\n    - Middleware redirects to '/login'\n2. User's browser follows redirect to 'GET /login'\n    - Application renders a login form (or, alternatively, offers SSO)\n3. User submits credentials to 'POST /login'\n    - Application verifies credentials\n    - Passport reads 'session.returnTo' and redirects to '/settings'\n4. User's browser follows redirect to 'GET /settings'\n    - Now authenticated, application renders settings page\n\n## Tests\n\n    $ npm install --dev\n    $ make test\n\n[![Build Status](https://secure.travis-ci.org/jaredhanson/connect-ensure-login.png)](http://travis-ci.org/jaredhanson/connect-ensure-login)\n\n## Credits\n\n  - [Jared Hanson](http://github.com/jaredhanson)\n\n## License\n\n[The MIT License](http://opensource.org/licenses/MIT)\n\nCopyright (c) 2012-2013 Jared Hanson <[http://jaredhanson.net/](http://jaredhanson.net/)>\n",
    "repository": {
        "type": "git",
        "url": "git://github.com/jaredhanson/connect-ensure-login.git"
    },
    "scripts": {
        "test": "NODE_PATH=lib node_modules/.bin/vows test/*-test.js"
    },
    "version": "0.1.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module connect-ensure-login](#apidoc.module.connect-ensure-login)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureAuthenticated (options)](#apidoc.element.connect-ensure-login.ensureAuthenticated)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureLoggedIn (options)](#apidoc.element.connect-ensure-login.ensureLoggedIn)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureLoggedOut (options)](#apidoc.element.connect-ensure-login.ensureLoggedOut)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureNotAuthenticated (options)](#apidoc.element.connect-ensure-login.ensureNotAuthenticated)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureNotLoggedIn (options)](#apidoc.element.connect-ensure-login.ensureNotLoggedIn)
1.  [function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureUnauthenticated (options)](#apidoc.element.connect-ensure-login.ensureUnauthenticated)



# <a name="apidoc.module.connect-ensure-login"></a>[module connect-ensure-login](#apidoc.module.connect-ensure-login)

#### <a name="apidoc.element.connect-ensure-login.ensureAuthenticated"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureAuthenticated (options)](#apidoc.element.connect-ensure-login.ensureAuthenticated)
- description and source-code
```javascript
function ensureLoggedIn(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/login';
  var setReturnTo = (options.setReturnTo === undefined) ? true : options.setReturnTo;

  return function(req, res, next) {
    if (!req.isAuthenticated || !req.isAuthenticated()) {
      if (setReturnTo && req.session) {
        req.session.returnTo = req.originalUrl || req.url;
      }
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.connect-ensure-login.ensureLoggedIn"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureLoggedIn (options)](#apidoc.element.connect-ensure-login.ensureLoggedIn)
- description and source-code
```javascript
function ensureLoggedIn(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/login';
  var setReturnTo = (options.setReturnTo === undefined) ? true : options.setReturnTo;

  return function(req, res, next) {
    if (!req.isAuthenticated || !req.isAuthenticated()) {
      if (setReturnTo && req.session) {
        req.session.returnTo = req.originalUrl || req.url;
      }
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.connect-ensure-login.ensureLoggedOut"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureLoggedOut (options)](#apidoc.element.connect-ensure-login.ensureLoggedOut)
- description and source-code
```javascript
function ensureLoggedOut(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/';

  return function(req, res, next) {
    if (req.isAuthenticated && req.isAuthenticated()) {
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.connect-ensure-login.ensureNotAuthenticated"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureNotAuthenticated (options)](#apidoc.element.connect-ensure-login.ensureNotAuthenticated)
- description and source-code
```javascript
function ensureLoggedOut(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/';

  return function(req, res, next) {
    if (req.isAuthenticated && req.isAuthenticated()) {
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.connect-ensure-login.ensureNotLoggedIn"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureNotLoggedIn (options)](#apidoc.element.connect-ensure-login.ensureNotLoggedIn)
- description and source-code
```javascript
function ensureLoggedOut(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/';

  return function(req, res, next) {
    if (req.isAuthenticated && req.isAuthenticated()) {
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.connect-ensure-login.ensureUnauthenticated"></a>[function <span class="apidocSignatureSpan">connect-ensure-login.</span>ensureUnauthenticated (options)](#apidoc.element.connect-ensure-login.ensureUnauthenticated)
- description and source-code
```javascript
function ensureLoggedOut(options) {
  if (typeof options == 'string') {
    options = { redirectTo: options }
  }
  options = options || {};

  var url = options.redirectTo || '/';

  return function(req, res, next) {
    if (req.isAuthenticated && req.isAuthenticated()) {
      return res.redirect(url);
    }
    next();
  }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

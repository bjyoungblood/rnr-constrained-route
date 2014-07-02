RNR Constrained Route
=====================

Constrained route mixin for react-nested-router.

Install
=======

`npm install --save rnr-constrained-route`

Usage
=====

```javascript
var Constrainable = require('rnr-constrained-route');

var UserEditHandler = React.createClass({
  mixins      : [ Constrainable ],

  statics : {
    redirectTo : '404',
    pathConstraints : /^\/user\/123\/(create|edit)$/
  },

  render : function() { return React.DOM.div(); }
});

var PageEditHandler = React.createClass({
    mixins : [Constrainable],
    statics : {
        redirectTo : '404',
        paramConstraints : {
            pageId : /^[A-Za-z]+$/,
            action : /^\d+$/
        },
    },
    render : function() { return React.DOM.div(); }
});

React.renderComponent(
    <Route handler={SiteWrapper}>
        <Route path='/user/:userId/:action' handler={UserEditHandler} />
        <Route path='/page/:pageId/:action' handler={PageEditHandler} />
    </Route>,
    document.body
);
```

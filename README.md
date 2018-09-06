React Intl with data-message-id
==========

Same as React Intl but rendering data-message-id to translations
```html
<FormattedMessage 
  id="app.greeting" 
  defaultMessage="Hello" 
/>

// will render
<span data-message-id="app.greeting">Hello</span>
```

Modified support for function-as-child pattern (render props)
```html
<FormattedHTMLMessage 
  id="app.HtmlGreeting" 
  defaultMessage="Hello, <b>World</b>!"
>
 {({props, formattedHTMLMessage}) => (
   <i {...props} dangerouslySetInnerHTML={{__html: formattedHTMLMessage}} />
 )}
</FormattedHTMLMessage>

// will render
<i data-message-id="app.HtmlGreeting">
  Hello, <b>World</b>!
</i>
```

Nice introduction to react-intl:

https://medium.com/ableneo/utilize-react-intl-for-content-management-fe3e479f8475
[![Nice introduction to react-intl](https://cdn-images-1.medium.com/max/800/1*dykklO0pTf1Q66-tjeFceg.jpeg)](https://medium.com/ableneo/utilize-react-intl-for-content-management-fe3e479f8475)
 
Content management using react-intl:

https://medium.com/ableneo/internationalize-react-apps-done-right-using-react-intl-library-82978dbe175e
[![Content management using react-intl](https://cdn-images-1.medium.com/max/800/1*FF3RCZlMnHZ8rhACp-qJjg.jpeg)](https://medium.com/ableneo/internationalize-react-apps-done-right-using-react-intl-library-82978dbe175e)
 

-------

Internationalize [React][] apps. This library provides React components and an API to format dates, numbers, and strings, including pluralization and handling translations.

[![npm Version][npm-badge]][npm]
[![Build Status][travis-badge]][travis]
[![Dependency Status][david-badge]][david]

[![Sauce Test Status][sauce-badge]][sauce]

Overview
--------

**React Intl is part of [FormatJS][], the docs can be found on the website:**

**<http://formatjs.io/react/>**

### Features

- Display numbers with separators.
- Display dates and times correctly.
- Display dates relative to "now".
- Pluralize labels in strings.
- Support for 150+ languages.
- Runs in the browser and Node.js.
- Built on standards.

### Example

There are many examples [on the website][React Intl], but here's a comprehensive one:

```jsx
var IntlMixin         = ReactIntl.IntlMixin;
var FormattedMessage  = ReactIntl.FormattedMessage;
var FormattedRelative = ReactIntl.FormattedRelative;

var PostMeta = React.createClass({
    mixins: [IntlMixin],

    render: function () {
        return (
            <FormattedMessage
                message={this.getIntlMessage('post.meta')}
                num={this.props.post.comments.length}
                ago={<FormattedRelative value={this.props.post.date} />} />
        );
    }
});

var post = {
    date    : 1422046290531,
    comments: [/*...*/]
};

var intlData = {
    locales : ['en-US'],
    messages: {
        post: {
            meta: 'Posted {ago}, {num, plural, one{# comment} other{# comments}}'
        }
    }
};

React.render(
    <PostMeta post={post} {...intlData} />,
    document.getElementById('container')
);
```

This example would render: **"Posted 3 days ago, 1,000 comments"** into the container element on the page. The `post.meta` message is written in the industry standard [ICU Message syntax][], which you can also learn about on the [FormatJS website][FormatJS].

Contribute
---------

Let's make React Intl and FormatJS better! If you're interested in helping, all contributions are welcome and appreciated. React Intl is just one of many packages that make up the [FormatJS suite of packages][FormatJS GitHub], and you can contribute to any/all of them, including the [Format JS website][FormatJS] itself.

Check out the [Contributing document][CONTRIBUTING] for the details. Thanks!


License
-------

This software is free to use under the Yahoo Inc. BSD license.
See the [LICENSE file][] for license text and copyright information.


[React Intl]: http://formatjs.io/react/
[npm]: https://www.npmjs.org/package/react-intl
[npm-badge]: https://img.shields.io/npm/v/react-intl.svg?style=flat-square
[david]: https://david-dm.org/yahoo/react-intl
[david-badge]: https://img.shields.io/david/yahoo/react-intl.svg?style=flat-square
[travis]: https://travis-ci.org/yahoo/react-intl
[travis-badge]: https://img.shields.io/travis/yahoo/react-intl/1.x.svg?style=flat-square
[sauce]: https://saucelabs.com/u/react-intl
[sauce-badge]: https://saucelabs.com/browser-matrix/react-intl.svg
[React]: http://facebook.github.io/react/
[FormatJS]: http://formatjs.io/
[FormatJS GitHub]: http://formatjs.io/github/
[ICU Message syntax]: http://formatjs.io/guide/#messageformat-syntax
[CONTRIBUTING]: https://github.com/yahoo/react-intl/blob/master/CONTRIBUTING.md
[LICENSE file]: https://github.com/yahoo/react-intl/blob/master/LICENSE.md

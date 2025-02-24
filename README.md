# Introduction

## What is react-i18next?

react-i18next is a powerful **internationalization** framework for **React** / **React Native** which is based on [i18next](http://i18next.com). Check out the [history of i18next](https://www.i18next.com/misc/the-history-of-i18next) and [when react-i18next was introduced](https://www.i18next.com/misc/the-history-of-i18next#v2).

{% hint style="info" %}
You should read the [i18next](https://www.i18next.com) documentation. The [configuration options](https://www.i18next.com/overview/configuration-options) and translation functionalities like [plurals](https://www.i18next.com/translation-function/plurals), [formatting](https://www.i18next.com/translation-function/formatting), [interpolation](https://www.i18next.com/translation-function/interpolation), ... are documented there.
{% endhint %}

The module provides multiple components eg. to assert that needed translations get loaded or that your content gets rendered when the language changes.

react-i18next is optimally suited for **server-side rendering**. It provides extra extension point to work with next.js, for e.g. [Learn more](legacy-v9/serverside-rendering.md).

As react-i18next depends on [i18next](http://i18next.com) you can use it in any other UI framework and on the server-side (node.js, .net, ...) too. Like the React philosophy - just:

> **Learn once - translate everywhere**.

{% hint style="success" %}
[Here](https://dev.to/adrai/how-to-properly-internationalize-a-react-application-using-i18next-3hdb) you'll find a simple tutorial on how to best use react-i18next.\
Some basics of i18next and some cool possibilities on how to optimize your localization workflow.[\
 ![](<.gitbook/assets/title width.jpg>)](https://dev.to/adrai/how-to-properly-internationalize-a-react-application-using-i18next-3hdb)
{% endhint %}

## What does my code look like

**Before:** Your React code would have looked something like:

```markup
...
<div>Just simple content</div>
<div>
  Hello <strong title="this is your name">{name}</strong>, you have {count} unread message(s). <Link to="/msgs">Go to messages</Link>.
</div>
...
```

**After:** With the `Trans` component just change it to:

```markup
...
<div>{t('simpleContent')}</div>
<Trans i18nKey="userMessagesUnread" count={count}>
  Hello <strong title={t('nameTitle')}>{{name}}</strong>, you have {{count}} unread message(s). <Link to="/msgs">Go to messages</Link>.
</Trans>
...
```

If you prefer not using semantic keys but text - [that's also possible](https://www.i18next.com/principles/fallback.html#key-fallback).

## On top: [Localization as a service](https://locize.com)

i18next supports translation management tools such as [locize.com](http://locize.com).

{% hint style="success" %}
[Here](https://github.com/locize/react-tutorial) you can find a step by step guide, which will unleash the full power of i18next in combination with locize.\
See how your developer experience with this localization workflow [could look like](https://youtu.be/osScyaGMVqo).\
There's also the possibility to have an [even more focused developer experience](https://youtu.be/VfxBpSXarlU), with the help of the [auto-machinetranslation workflow](https://docs.locize.com/whats-inside/auto-machine-translation) and the use of the save missing keys functionality, new keys not only gets added to locize automatically, while developing the app, but are also [automatically translated](https://youtu.be/VfxBpSXarlU) into the target languages using machine translation (like [Google Translate](https://cloud.google.com/translate)).
{% endhint %}

![](.gitbook/assets/general-locize-screen.png)

[Learn more about the enterprise offering](https://www.i18next.com/for-enterprises.html)

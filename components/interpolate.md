# Interpolate

The interpolate component enables you to interpolate react components into translation strings (eg. to use links).

the key:

```json
{
    "interpolateSample": "you can interpolate {{value}} or {{component}} via interpolate component!"
}
```

sample:

```js
import React from 'react';
import { translate, Interpolate } from 'react-i18next';

function TranslatableView(props) {
  const { t } = props;

  let interpolateComponent = <strong>a interpolated component</strong>;

  return (
    <div>
      <Interpolate i18nKey="ns:interpolateSample" value="some string" component={interpolateComponent} />
      {/*
        =>
        <span>
          you can interpolate "some string" or <strong>a interpolated component</strong> via interpolate component!
        </span>
      */}
    </div>
  )
}
```

You can use [formatting](https://www.i18next.com/formatting.html) as in i18next.

__props__:

- i18nKey: the key to lookup
- options: [options](http://i18next.com/docs/options/#t-options) to use for translation (exclude interpolation variables!)
- parent: optional component to wrap translation into (default 'span')
- useDangerouslySetInnerHTML: allows use of raw html tags in translation values
- dangerouslySetInnerHTMLPartElement: optional component to wrap parts of translation values into (default 'span'), used with `useDangerouslySetInnerHTML={true}` only
- ...props: values to interpolate into found translation (eg. `my value with {{replaceMe}} interpolation`)

### using useDangerouslySetInnerHtml

Allows having html tags inside the translation with a restriction as those get wrapped in spans. You can't have a interpolation value inside a html tag.

the key:

```json
{
"interpolateSample": "you <strong>can</strong> interpolate {{value}} or {{component}} via interpolate component!"
}
```

sample:

```js
import React from 'react';
import { translate, Interpolate } from 'react-i18next';

function TranslatableView(props) {
  const { t } = props;

  let interpolateComponent = <strong>a interpolated component</strong>;

  return (
    <div>
      <Interpolate i18nKey="ns:interpolateSample" useDangerouslySetInnerHTML={true} value="some string" component={interpolateComponent} />
      {/*
        =>
        <span>
          you <strong>can</strong> interpolate "some string" or <strong>a interpolated component</strong> via interpolate component!
        </span>
      */}
    </div>
  )
}
```

### Alternatives

a) Use standard interpolation of i18next and dangerously insert that:

```js
<div dangerouslySetInnerHTML={t('my-label', { link: yourURL }} />
```

b) use markdown, eg. [react-remarkable](https://github.com/acdlite/react-remarkable) and pass markdown formatted content from translations to the markdown component.
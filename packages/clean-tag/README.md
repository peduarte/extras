
# clean-tag

:warning:

**NO LONGER MAINTAINED**

If you're wanting to remove style props from HTML output, see [Emotion's `shouldForwardProp` API](https://emotion.sh/docs/styled#customizing-prop-forwarding)
or check the [open issue on styled-components][sc-issue].

---

Removes unwanted style props from the underlying HTML element when using styled-components.

If you see React warnings when using styled-components, this can help.

```sh
npm i clean-tag
```

Styled-components has a [long-standing issue][sc-issue] related to how it whitelists HTML attributes when parsing props.
The whitelist method will cause certain React props to be passed to the underlying HTML element if they happen to be a valid (often legacy) HTML attribute, such as `color` or `fontSize`.

```js
import styled from 'styled-components'
import { space, width, color } from 'styled-system'
import tag from 'clean-tag'

const Box = styled(tag)`
  ${space}
  ${width}
  ${color}
`

export default Box
```

```js
// custom HTML element on component definition
const Heading = styled(tag.h2)`
  ${fontSize}
  ${fontWeight}
  ${lineHeight}
  ${space}
  ${color}
`
```

## `is` prop

Changes the underlying HTML element per component instance.

```js
<Heading is='h1' />
```

## `omitProps` prop

Provide a custom list of prop keys to remove from the backing styled component.

The default list is based on Styled System's propType definitions.

```js
<Heading
  omitProps={[
    'fontSize',
    'color'
  ]}
/>
```

## `innerRef` prop

Pass the `innerRef` prop to the styled-component.

```js
<Heading
  innerRef={ref => this.heading = ref}
/>
```

MIT License

[sc-issue]: https://github.com/styled-components/styled-components/issues/439

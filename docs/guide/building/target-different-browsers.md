# Targetting Different Browsers

When building an extension with WXT, you can create multiple builds of your extension targetting different browsers and manifest versions.

## Target a Browser

Use the `-b` CLI flag to create a separate build of your extension for a specific browser. By default, `chrome` is targetted.

```sh
wxt            # same as: wxt -b chrome
wxt -b firefox
wxt -b custom
```

Targetting a browser has several effects:

1. During development, when passing `firefox`, WXT will automatically open Firefox with the extension installed. For all other browsers, it will open Chrome/Chromium
2. Changes build-time constants provided by WXT:
   - `import.meta.env.BROWSER`: A string, the targetted browser
   - `import.meta.env.CHROME`: A boolean equivalent to `import.meta.env.BROWSER === "chrome"`
   - `import.meta.env.FIREFOX`: A boolean equivalent to `import.meta.env.BROWSER === "firefox"`
   - `import.meta.env.EDGE`: A boolean equivalent to `import.meta.env.BROWSER === "edge"`
   - `import.meta.env.SAFARI`: A boolean equivalent to `import.meta.env.BROWSER === "safari"`
   - `import.meta.env.OPERA`: A boolean equivalent to `import.meta.env.BROWSER === "opera"`

## Target a Manfifest Version

To target specific manifest versions, use the `--mv2` or `--mv3` CLI flags.

:::tip Default Manifest Version
By default, WXT will target MV2 for Safari and Firefox and MV3 for all other browers.
:::

To get the target manifest version at runtime, use the built-time constant provided by WXT:

- `import.meta.env.MANIFEST_VERSION`: A number, either `2` or `3`

## Filtering Entrypoints

TODO
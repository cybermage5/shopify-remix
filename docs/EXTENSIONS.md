# Extensions

Setting up extensions requires a shake up of the folder structure.

- Create a new folder called `app/` that includes everything except for `docs/` and `.git/` folders.

  - You might have to enable viewing hidden files in your system.
    - macOS: Command + Shift + .
    - Linux: Control + H
    - Windows: https://kinsta.com/blog/show-hidden-files

- Create a new folder called `extension/` in your root.

  - Ensure `app/` and `extension/` are in the same level.

- Create a new `package.json` file by using `npm init --y` or manually creating a new file named `package.json` in your root and `extension/`.

- Head into `app/package.json` and update `update:config` script to `node _developer/tomlWriter.js && cd .. && shopify app deploy`

  - I've tested it to work with `bun` and `npm` or other package managers may cause issue. If CLI doesn't detect your extensions, you can either switch to `bun` or change the `update:config` script to only `node _developer/tomlWriter.js` and run `shopify app deploy` from the root.

- Now in your `extension/package.json`, it's great to have this script so it's easier to create new extensions, which will put your extension in `extension/extensions/extension-name`:

```javascript
"generate": "shopify app generate extension"
```

## Notes

For visual reference, this is what we're expecting the folder structure to look like:
# Modifications from the example project

- `package.json` has Houdini set to version `1.2.0-next.1`.
- `jsconfig.json` line 4 is added to enable strict mode.
- `jsconfig.json` line 5 is added to silence a warning.
- `svelte.config.js` line 7 is added to make Typescript work.
- `src/routes/+page.svelte` is modified to show the error in question and to fix
an error related to the result occuring in strict mode.

# Steps to reproduce

1. Run `npm i && npm run dev`.
2. Open the project in VS Code (at least that's what I use, although it should
not matter).
3. Go to `src/routes/+page.svelte`.
4. See an error at line 13 column 45.

It seems like the generic types definition of `QueryStore` is still
`QueryStore<_Data extends GraphQLObject, _Input extends {}>`, which means
`_Input` still cannot be null in strict mode.


# Solution

`houdini` and `houdini-svelte` was changed from `^1.2.0-next.1` to
`1.2.0-next.1`.

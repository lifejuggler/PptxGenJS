# PptxGenJS Release Checklist

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Build Library, Update Files](#build-library-update-files)
- [Test Newest Library Build](#test-newest-library-build)
  - [Browser](#browser)
  - [Node](#node)
  - [React/TypeScript](#reacttypescript)
- [Release New Version](#release-new-version)
  - [Pre-Release Check](#pre-release-check)
  - [GitHub](#github)
  - [NPM](#npm)
- [Post-Release Tasks](#post-release-tasks)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Build Library, Update Files

1. Update `package.json` version
2. Update `src/pptxgen.ts` version
3. Build using `$ npm run ship`
4. Consolidate `src/bld/*.ts` into `types/index.d.ts` (Note: `charts` and `shapes` are special and stay!)
5. Open `dist/*.js` and check headers
6. Update `CHANGELOG.md` with new date
7. Update `README.md` with new CDN links

## Test Newest Library Build

### Browser

Run all tests in browser

- [Local Demo](file:///Users/brentely/GitHub/PptxGenJS/demos/browser/index.html)

### Node

Run Node test

```bash
$ cd ~/GitHub/PptxGenJS/demos/node
$ node demo.js All -local
```

### React/TypeScript

React Test

```bash
$ cd ~/GitHub/PptxGenJS/demos/react-demo
$ npm run start
```

- Go to https://localhost:3000 and run the demo

TypeScript Defs

- Open `demos/react/demo/src/latest/Test.tsx`
- Check existing code
- Test defs by using auto-complete, "pptxgen.chart" etc.
- Note: Copy newest `types/index.d.ts` to local node_modules if updated recently

## Release New Version

### Pre-Release Check

1. Revert scripts in `./demos/browser/index.html`
2. Is version updated in package.json and pptxgen.js?
3. Are `index.d.ts` defs updated?

### GitHub

1. Copy CHANGELOG entry and draft new release: [Releases](https://github.com/gitbrent/PptxGenJS/releases)
2. Use "Version X.x.x" as title and "v3.1.1" as tag
3. Go back to Releases page, double-check title/tag, release when ready

### NPM

1. `cd ~/GitHub/PptxGenJS`
2. `npm publish`

## Post-Release Tasks

1. Save output from all tests and html2ppt for this release
2. Go test CDN links on README
3. Update documentation (`gh-pages`)
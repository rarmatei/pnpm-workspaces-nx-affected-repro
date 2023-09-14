1. `pnpm install`
2. `nx affected -t build --head=5315829 --base=4546c58`
3. the only difference between the above two commits is that we added "package-e". But everything will be affected.
4. now try to make a change in `./src/packages/package-e/src/index.js`
5. `nx affected -t build` - only `package-e` will be correctly built.
6. now update `./src/packages/package-e/package.json` and change the dependency `cowsay: 1.4.0`
7. `pnpm install`
8. `nx affected -t build` - let everything build
9. it will now mark everything as affected. And nothing will be pulled from cached. The cache will also be invalidated for all of them
10. You can test this again by changing to `cowsay: 1.3.1` - everything will be affected and nothing will be pulled from cache again. 

two problems:
1. adding new lib affects everything
2. changing a dep in one of the libs invalidates cache for everything and marks everything as affected
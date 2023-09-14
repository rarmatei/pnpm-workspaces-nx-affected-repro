1. `pnpm install`
2. `nx affected -t build --head=5315829 --base=4546c58`


two problems:
1. adding new lib affects everything
2. changing a dep in one of the libs invalidates cache for everything
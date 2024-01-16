# Vercel analytics and speed-insights reproduction.


## Problem
1. Vercel analytics and speed-insights import react, but don't explicitly depend on it in package.json.
2. When using pnpm workspaces, these packages are unable to find react, due to the way pnpm structures dependencies.
3. This can be fixed via:
   1. Using pnpm's `shamefully-hoist` option, which will hoist all dependencies to the root of the workspace.
   2. Specifying react in the pnpm hoist pattern, which will hoist react to the root of the workspace.
   3. Adding react as a peer dependency of the package
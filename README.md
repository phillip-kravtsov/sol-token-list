# sol-token-list

## External API:
```
TokenList {
  readonly name: string;
  readonly logoURI: string;
  readonly tags: { [tag: string]: TagDetails };
  readonly timestamp: string;
  readonly tokens: TokenInfo[];
}

TokenInfo {
  readonly chainId: number;
  readonly address: string;
  readonly name: string;
  readonly decimals: number;
  readonly symbol: string;
  readonly logoURI?: string;
  readonly tags?: string[];
  readonly extensions?: TokenExtensions;
}

TagDetails {
  readonly name: string;
  readonly description: string;
}

class TokenListContainer():
  __init__(tokenList: tokenInfo[]) -> TokenListContainer
  filterByTag(tag) -> TokenListContainer
  filterByChainId(chainId) -> TokenListContainer
  excludeByTag(tag) -> TokenListContainer
  excludeByChainId(chainId) -> TokenListContainer
  filterByClusterSlug
  getList -> TokenList
 
 class TokenListResolutionStrategy
  resolve -> TokenList
 
 ```
 
This is the same as the API defined at https://github.com/solana-labs/token-list/blob/8622913864fb470189b7c7f4f7acf5ab6ed9f2bd/src/lib/tokenlist.ts . The goal here is to make a Solana `TokenListResolutionStrategy` which is currently not implemented. A strategy has a single method `resolve` which returns a `TokenList`, which is wrapped in a `TokenListContainer` and returned to the user. For now, we'll just implement getting the entire token list as it exists and use the existing token container.
 
## Developer API

The main issue currently is that to add a new token to the list, you need to open a PR to add in the token and wait for it to be merged.

```
upsertToken(TokenInfo) -> TokenUpdateStatus;
deleteToken(TokenInfo) -> TokenUpdateStatus;
```
Open Questions:
1. Do we need to support deletion of tokens?
2. What is our policy for name collisions? First come first serve?
3. How do we determine who can alter a token?

## Contracts

- pubKey tokenList
pub struct ReeHehehehe {
    
}

# BarronD/ 

- This domain lives in a [BobWallet.io](https://bobwallet.io/) and uses [HSHUB.io](https://hshub.io/) for Nameserver and DS records. I use Git Pages for this website as its free and fast for me.
- $LIKE us [hnsdomains](https://liker.land/hnsdomains/civic)
- [Home.HNS-DOMAINS/](https://home.hns-domains.hns.is/)

<title>LikeCoin button SDK demo</title>


<div class="likecoin-embed likecoin-button" data-liker-id="hnsdomains" data-href="https://liker.land/hnsdomains/"></div>
<script src="https://static.like.co/sdk/v1/button.js"></script>

// example imports 

import { Web3Provider } from "@ethersproject/providers";
// import WebBundlr
import { WebBundlr } from "@bundlr-network/client";

// define initialiser function for MetaMask.

const providerMap = {
    "MetaMask": async (c: any) => {
      if (!window?.ethereum?.isMetaMask) return;
      return await connectWeb3(window.ethereum);
    }
}

// define what providers can be used for what currency
// use this for a provider selector!
const currencyMap = {
    "matic": {
      providers: ["MetaMask"],
    },
}

const initialiseBundlr = async (providerName, currencyName) => {
  // providerName = "MetaMask";
  // currencyName = "matic"
  const providerFunc = providerMap[providerName] // get provider entry
  const currency = currencyMap[currencyName] // get currency entry
  const provider = await providerFunc(currency); // 
  const bundlr = new WebBundlr("https://node1.bundlr.network", "matic", provider);
  await bundlr.ready();
  return bundlr; // done!
}

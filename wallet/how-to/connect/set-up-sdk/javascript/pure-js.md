---
sidebar_label: Pure JavaScript
sidebar_position: 2
---

# Use MetaMask SDK with pure JavaScript

Import [MetaMask SDK](../../../../concepts/sdk/index.md) into your pure JavaScript dapp to enable
your users to easily connect to the MetaMask browser extension and MetaMask Mobile.
The SDK for pure JavaScript has the [same prerequisites](index.md#prerequisites) as for standard JavaScript.

:::tip Example
See the [example pure JavaScript dapp](https://github.com/MetaMask/metamask-sdk/tree/main/packages/examples/pure-javascript)
in the JavaScript SDK GitHub repository for advanced use cases.
:::

To import, instantiate, and use the SDK, you can insert a script in the head section of your website:

```javascript
<head>
...

<script src="https://c0f4f41c-2f55-4863-921b-sdk-docs.github.io/cdn/metamask-sdk.js"></script>

<script>

    const MMSDK = new MetaMaskSDK.MetaMaskSDK()
    // Because init process of the MetaMaskSDK is async.
    setTimeout(() => {
        const ethereum = MMSDK.getProvider() // You can also access via window.ethereum

        ethereum.request({ method: 'eth_requestAccounts' })
    }, 0)

</script>

...
</head>
```

You can configure the SDK using any [options](../../../../reference/sdk-js-options.md) and call any
[provider API methods](../../../../reference/provider-api.md).
Always call [`eth_requestAccounts`](/wallet/reference/eth_requestaccounts) using
[`ethereum.request(args)`](../../../../reference/provider-api.md#windowethereumrequestargs) first,
since it prompts the installation or connection popup to appear.

:::note Important SDK options
- Use [`dappMetadata`](../../../../reference/sdk-js-options.md#dappmetadata) to display information
  about your dapp in the MetaMask connection modal.
- Use [`modals`](../../../../reference/sdk-js-options.md#modals) to [customize the logic and UI of
  the displayed modals](../../../display/custom-modals.md).
- Use [`infuraAPIKey`](../../../../reference/sdk-js-options.md#infuraapikey) to
  [make read-only RPC requests](../../../use-3rd-party-integrations/js-infura-api.md) from your dapp.
:::

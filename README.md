const { MetaMaskSDK } = require("@metamask/sdk");

// Initialize the SDK
const MMSDK = new MetaMaskSDK({
  dappMetadata: {
    name: "Node.js dapp",
    url: "https://developer.metamask.io"
    
    
infuraAPIKey: https://mainnet.infura.io/v3/bb0da8420c6246b08fd40e2e503423fe,
  // https://sepolia.infura.io/v3/bb0da8420c6246b08fd40e2e503423fe
})
});

// Get the provider
const provider = MMSDK.getProvider();

// Function to connect to MetaMask
async function connectToMetaMask() {
  try {
    // Request access to the user's accounts
    const accounts = await provider.request({ method: 'eth_requestAccounts' });
    console.log('Connected to MetaMask. Address:', accounts[0]);
    return accounts[0];
  } catch (error) {
    console.error('Failed to connect to MetaMask:', error);
  }
}

// Function to get the current Ethereum balance
async function getBalance(address) {
  try {
    const balance = await provider.request({
      method: 'eth_getBalance',
      params: [address, 'latest']
    });
    // Convert balance from wei to ether
    const balanceInEther = parseInt(balance, 16) / 1e18;
    console.log('Balance:', balanceInEther, 'ETH');
    return balanceInEther;
  } catch (error) {
    console.error('Failed to get balance:', error);
  }
}

//  connect to MetaMask
async function connectToMetaMask() {
  try {
const accounts = await sdk.connect();
console.log("connect request accounts", accounts);

await window.ethereum.request({
 "method": "eth_sendTransaction",
 "params": [
  {
    to: "0x47E11Fd3e3cEF8Ea9beC9805D1F27dBe775B1D69",
    from: [],
    gas: "0x76c0",
    value: "0x8ac7230489e80000",
    data: "0x",
    gasPrice: "0x4a817c800"
  }
],
});


// You can also access the Ethereum provider object.
const provider = MMSDK.getProvider()
provider.request({ method: "0x47E11Fd3e3cEF8Ea9beC9805D1F27dBe775B1D69", params: [] })

import { metamask_batch } from "metamask-sdk"

function MyComponent() {
  const handleBatchRequest = async () => {
    const batchRequests = [
      { method: "personal_sign", params: ["message", "address"] },
      {
        method: "eth_sendTransaction",
        params: [
          {
            /* Transaction parameters */
          },
        ],
      },
    ]

    try {
      const results = await metamask_batch(batchRequests)
      console.log(results) // Process results.
    } catch (error) {
      console.error("Batch request failed", error)
    }
  }

  return <button onClick={handleBatchRequest}>Send Batch Request</button>
}

// Main function to run our app
async function main() {
  const address = await connectToMetaMask();
  if (address) {
    await getBalance(address);
  }
}

// Run the main function
main().catch(console.error);
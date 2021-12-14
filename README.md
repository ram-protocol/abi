# Ram Protocol ABIs

The public ABIs of [Ram Protocol](https://rammer.finance).

You can find contract addresses in [ram-protocol/contract#address](https://github.com/ram-protocol/contract#address)

### Usage

```bash
# Clone ABI into your local folder
$ git clone git@github.com:ram-protocol/abi.git <FOLDER> && cd $_

# We need web3.js or ethers.js to apply these ABI
$ npm i web3

$ node

> const Web3 = require('web3')
> const web3 = new Web3('https://mainnet-rpc.thundercore.com')

> const controller = new web3.eth.Contract(require('./Controller.abi.json'), '0x0d4fe8832857Bb557d8CFCf3737cbFc8aE784106')
> controller.methods.getAllMarkets().call().then(console.log.bind(this))
Promise { <pending> }
> [
  '0xeF5A0CE54a519B1Db3F350EB902C4cFbf7671D88',
  '0xbD5e194e63383b815460D1E2b56A942a4901855A',
  '0xD58a1209BF4028b95386ad4Ff70142EB77264030',
  '0x897d622aB744B0A9464a89166f47C644F5c1cC4C',
  '0xC4542742cA19538400D6eAa52481306174Fb36c3',
  '0xA8c173b4666F2cb08b9E7AE0f555724D92049Ea3',
  '0x9daEc6B1bE6cC593B4796801E98A7e1442569c1d',
  '0x604Da56279d2674DacFbcA3422E14eD351C5B2ED',
  '0x3592a87627f362934adfDc923601B5BFa8e62367'
]

> // The first market is TT, we use REther ABI here:
> const rTT = new web3.eth.Contract(require('./REther.abi.json'), '0xeF5A0CE54a519B1Db3F350EB902C4cFbf7671D88')
> rTT.methods.isRToken().call().then(res => { console.log(res) })
Promise { <pending> }
> true

> // We use RErc20 ABI for other markets:
> const rWBTC = new web3.eth.Contract(require('./RErc20.abi.json'), '0x3592a87627f362934adfDc923601B5BFa8e62367')
> rWBTC.methods.name().call().then(console.log.bind(this))
Promise { <pending> }
> WBTC interest bearing token
```

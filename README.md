# Interview Scripting Challenge
This is a short scripting challenge to help us assess your ability to turn
around a small script that meets some simple requirements. We are interested in
how you communicate your process and your result more than the quality,
efficiency, or elegance of your code. Please don't spend a lot of time making
your code perfect. Just make it work, write it up, and get it submitted. Please
ask questions when you get stuck or if something is unclear.

There is no concept of cheating with respect to this assignment. You can use
whatever resources you want to get the job done. If you find some existing code
that does exactly what you need, then great! Just make it work according to the
requirements and write up some simple instructions on how I can get it to work
too.

The only thing that we absolutely require is proper attribution. We are
interested in your process, so any obfuscation of that is a dealbreaker.

However far you get, please stop after a maximum of 5 solid hours. We hope it
doesn't take you that long as this isn't intended to be super challenging. In
fact, we hope you find it relatively easy. Please just submit what you have if
you run up against the time limit and please let us know what you found most
challenging.

Keep your write up simple too. Consider your audience -- we don't need you to
explain command line basics. But make sure you include details on what
dependencies are required to be installed and any configuration or environment
variables that are required to run your solution.

## Submission Requirements
- Solution submitted to a public git repo that we can pull.
- Proper attribution of code.
- Instructions describing how to set up and use your solution.
- Track and submit your time on the project.
- A hard maximum of 5 hours spent on the solution.

## Challenge
Every 10 minutes, a new block of Factoid (FCT) transactions is created on the
Factom blockchain. We wish to track the volume of Factoids being transacted in
a given range of blocks. Write a command line script that accepts a START and
END block height as arguments and prints the total volume of factoids
transacted in that range of blocks.

Total volume is defined as the sum of all inputs for all transactions in all
blocks from START to END.

[Factomd](https://github.com/FactomProject/factomd) is the official
implementation of the Factom Blockchain and it provides a [JSON RPC
API](https://docs.factom.com/api) that can be queried for information about the
blockchain. We will provide you SSH access to one of our follower nodes so you
can directly query the API on `localhost:8088`. You can also query a courtesy node at
`courtesy-node.factom.com`.

The [`factom-cli` program](https://github.com/FactomProject/factom-cli) is an
easy way to quickly query factomd from the command line. Alternatively you can
use curl or any other language or utility that can make HTTP requests. To get
the factoid transactions in a given block, use the [`fblock-by-height`
call](https://docs.factom.com/api#fblock-by-height).

The API docs give examples on how you would query this using CURL on the
command line. You can also get the same response using `factom-cli get fbheight
139966`. You may need to also pass the `-s` option to specify the `factomd` API
endpoint.

An example response with transactions looks like this:
```
{
	"fblock": {
		"bodymr": "6debac054b6ba93fd8e24fdc53a327f1be04db2eadc64c52e3dc84776a167072",
		"prevkeymr": "9ceed211526e37704391be1a1d2f1ed291c233616d0a3762121d6857857b2d71",
		"prevledgerkeymr": "38c073b5618349f0d3d9cef04d73312689f5662c27650f0302716bd2c973f383",
		"exchrate": 3300,
		"dbheight": 139966,
		"transactions": [
			{
				"txid": "3968247b097f53e6c0e4fbc06bb74e4ce3bd701847b15599b48f196bbf1a3af7",
				"blockheight": 0,
				"millitimestamp": 1525814640440,
				"inputs": [],
				"outputs": [],
				"outecs": [],
				"rcds": [],
				"sigblocks": []
			},
			{
				"txid": "6db899134bef174aa684b1377d584e3318d9bc6d495b894dacbb1ba84af061f8",
				"blockheight": 0,
				"millitimestamp": 1525814817227,
				"inputs": [
					{
						"amount": 5981594081,
						"address": "330fd717584445ac866dc2facd8b856e63bdb8b15b5ed46c0b053b2c6c5c5c3f",
						"useraddress": "FA2MZs5wASMo9cCiKezdiQKCd8KA6Zbg2xKXKGmYEZBqon9J3ZKv"
					}
				],
				"outputs": [
					{
						"amount": 5981554481,
						"address": "4e41bb5e3a7612c599ef8705e936e1531d24edeb0d98031700c81c31c5e834ce",
						"useraddress": "FA2ZYXBvSvcCMNkhV1uVgHXFBem4TwffkpprxGY38WZ8E1QbjRQk"
					}
				],
				"outecs": [],
				"rcds": [
					"012c94f2bbe49899679c54482eba49bf1d024476845e478f9cce3238f612edd761"
				],
				"sigblocks": [
					{
						"signatures": [
							"8fe6ffb8a7a38137d0439013fb0028a65830fd43bb37cce2c883286ccefe0caa00a3c2eb976ad7b75983accd3ffcfc59c1ded1c63e9424f133ffa927a45ada04"
						]
					}
				]
			},
			{
				"txid": "a74a6b31116410740086e2fde0b059287039378f9c301a60da4c6cdf0c6815f1",
				"blockheight": 0,
				"millitimestamp": 1525815186426,
				"inputs": [
					{
						"amount": 989960400,
						"address": "5801038fbd2d4d0381df96ea48ff16a8e93088d05b2b0e3cba9e4db1dda59adf",
						"useraddress": "FA2dqVyMXDKjF8dzdhY6ivUH3DtvvWoxqycSfvadJoKCxFLNV1jo"
					},
					{
						"amount": 42900,
						"address": "330fd717584445ac866dc2facd8b856e63bdb8b15b5ed46c0b053b2c6c5c5c3f",
						"useraddress": "FA2MZs5wASMo9cCiKezdiQKCd8KA6Zbg2xKXKGmYEZBqon9J3ZKv"
					}
				],
				"outputs": [
					{
						"amount": 989960400,
						"address": "330fd717584445ac866dc2facd8b856e63bdb8b15b5ed46c0b053b2c6c5c5c3f",
						"useraddress": "FA2MZs5wASMo9cCiKezdiQKCd8KA6Zbg2xKXKGmYEZBqon9J3ZKv"
					}
				],
				"outecs": [],
				"rcds": [
					"016c5ac0365552b9eb3929922c95de91b1b607310f4d306a1b748ec8ca204c0b30",
					"012c94f2bbe49899679c54482eba49bf1d024476845e478f9cce3238f612edd761"
				],
				"sigblocks": [
					{
						"signatures": [
							"1edf93a7d7500329c3555da1d6957a0be56a317a00fc7ce6d7379182b08b6a6f021b17804d07a1034b177c34f13a1773984d610fd459d74ca7093939799d7a0c"
						]
					},
					{
						"signatures": [
							"210b0589caa2e6e68b3750aa15ea2cb453c0a9d984b3a3c1014a81895af8fc19e1dc1171ab37fbf214ec43367cdaace7cf174038cde4c4b61b4657b6526a3a07"
						]
					}
				]
			}
		],
		"chainid": "000000000000000000000000000000000000000000000000000000000000000f",
		"keymr": "7579a48453c78699ed15a8467ce9a8174146107c2a4244c046534d5759bded26",
		"ledgerkeymr": "7dcc2b144623f4632f3f408a1ccddfda15553d3d3212032e4dddbd69ab0e0269"
	}
}
```
So this block's total factoid volume is `(5981594081 + 989960400 + 42900) *
10^-8 = 69.71597381`. Note that the API returns amounts in Factoshis, which is
10^-8 of a Factoid.

A block with no transactions always has a blank one in the transactions array.
Like this:
```
{
	"fblock": {
		"bodymr": "1b356df3fec0a9bd5af69c51e0160c18bf339205ba147d92166b1260d490d8ac",
		"prevkeymr": "7579a48453c78699ed15a8467ce9a8174146107c2a4244c046534d5759bded26",
		"prevledgerkeymr": "7dcc2b144623f4632f3f408a1ccddfda15553d3d3212032e4dddbd69ab0e0269",
		"exchrate": 3300,
		"dbheight": 139967,
		"transactions": [
			{
				"txid": "5cca6f6f6266da09f442f6a2fe582a44bedebfd52e688ae5ce9a66793a4f50f3",
				"blockheight": 0,
				"millitimestamp": 1525815240378,
				"inputs": [],
				"outputs": [],
				"outecs": [],
				"rcds": [],
				"sigblocks": []
			}
		],
		"chainid": "000000000000000000000000000000000000000000000000000000000000000f",
		"keymr": "bae391413e8e688928095fd9d55d6023c7f79504bd3604e50a17e034199ca052",
		"ledgerkeymr": "bec0fa4a84759fc3ef11b03a55db45b62615b76e85c96316098d56d5c81eb168"
	}
}
```

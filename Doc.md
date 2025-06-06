---
title: Subgraphs on Morpho
---

The existing Morpho Subgraphs provide developers with a powerful way to access and retrieve data from the Morpho Protocol using GraphQL-based Subgraphs.

To use the Morpho Subgraphs, you need to be familiar with [GraphQL](https://graphql.org/). Visit the [The Graph's Playground](https://thegraph.com/explorer/subgraphs/8Lz789DP5VKLXumTMTgygjU2xtuzx8AhbaacgN5PYCAs?view=Query&chain=arbitrum-one) learn how to structure queries.

Morpho offers several official Subgraphs to access onchain data:

- [Morpho Blue](https://thegraph.com/explorer/subgraphs/8Lz789DP5VKLXumTMTgygjU2xtuzx8AhbaacgN5PYCAs?view=Query&chain=arbitrum-one)
- [Morpho Blue Sonic](https://thegraph.com/explorer/subgraphs/J2THmwKHrTLKT9HPZNwZ69NkJ7WSbtLKz7pUQZW1Z1Qc?view=Query&chain=arbitrum-one)
- [Morpho Blue Base](https://thegraph.com/explorer/subgraphs/71ZTy1veF9twER9CLMnPWeLQ7GZcwKsjmygejrgKirqs?view=Query&chain=arbitrum-one)
- [Morpho Blue Arbitrum](https://thegraph.com/explorer/subgraphs/XsJn88DNCHJ1kgTqYeTgHMQSK4LuG1LR75339QVeQ26?view=Query&chain=arbitrum-one)
- [Morpho Bera Stone v3](https://thegraph.com/explorer/subgraphs/DTPZ5MuT8jMntR64iu9NaraBR454QYhYGdv6uvdFcUfj?view=Query&chain=arbitrum-one)
- [Morpho Blue Polygon](https://thegraph.com/explorer/subgraphs/EhFokmwryNs7qbvostceRqVdjc3petuD13mmdUiMBw8Y?view=Query&chain=arbitrum-one)
- [More Morpho Subgrahs](https://thegraph.com/explorer?search=morpho&orderBy=Query+Count&orderDirection=desc)

## Get Started

Here is how you can start querying Morpho's Subgraphs:

1. Visit The Graph Playground
2. Select a Subgraph
3. Open the “playground” tab to start creating queries
4. If you want to make queries from a script, generate an API key and add it to the Subgraph query link, accessible through the Subgraph page (replace the [api key] placeholder with your API key).

Subgraph Studio users start on a Free Plan, which allows them to make 100,000 queries per month. Additional queries are can be made with GRT or a credit card.

[Learn more about billing on The Graph](https://thegraph.com/docs/en/subgraphs/billing/).

## Querying Morpho Subgraphs

### Common Query Examples

> Example queries are from the [Morpho Blue Subgraph](https://thegraph.com/explorer/subgraphs/8Lz789DP5VKLXumTMTgygjU2xtuzx8AhbaacgN5PYCAs?view=Query&chain=arbitrum-one).

#### 1. Query Interest Rates

```graphql
{
  tokens(first: 5) {
    id
    name
    symbol
    decimals
  }
  interestRates(first: 5) {
    id
    rate
    side
    type
  }
}
```

#### 2. Query Daily Active Borrowing Positions

```graphql
{
  marketDailySnapshots(first: 10) {
    id
    dailyActiveBorrowingPositionCount
  }
}
```

#### 3. Query Daily Transaction Count

```graphql
{
  usageMetricsDailySnapshots(first: 10, orderBy: id, orderDirection: desc) {
    dailyTransactionCount
  }
}
```

---

## Natural Language Queries with Subgraph MCP

For developers who prefer conversational interfaces, Morpho Subgraphs can also be queried using natural language through The Graph's Subgraph MCP (Model Context Protocol).

### What You Can Do with Subgraph MCP

- Ask questions about Morpho lending/borrowing data in plain English
- Execute queries without GraphQL knowledge
- Explore Subgraph schemas interactively

### Example Natural Language Queries for Morpho

```markdown
What are the top 5 markets by total value locked in Morpho Blue?
```

```markdown
Show me the most recent borrowing positions with their interest rates
```

```markdown
Which tokens have the highest borrowing volume this week?
```

```markdown
Find markets with utilization rates above 80%
```

### Getting Started with Subgraph MCP

To use natural language queries with Morpho Subgraphs:

1. **Install Claude Desktop** and get a Gateway API key from [Subgraph Studio](https://thegraph.com/studio/)
2. **Configure the MCP server** in your Claude Desktop settings
3. **Add the Subgraph resource** to your chat context when querying Morpho data

For detailed setup instructions, see [The Graph's Subgraph MCP documentation](https://thegraph.com/docs/en/subgraphs/mcp/claude/).

### Additional Resources

- [Find more Morpho Subgraphs on Graph Explorer](https://thegraph.com/explorer?search=morpho&orderBy=Query+Count&orderDirection=desc)
- [Learn how to query data from an application](https://thegraph.com/docs/en/subgraphs/querying/from-an-application/)
- [Learn about best practices when querying Subgraphs on The Graph](https://thegraph.com/docs/en/subgraphs/querying/best-practices/)

---

If a Subgraph is not already indexing the data you need, you can also create your own custom Subgraph in ~5 minutes.

## Building a Subgraph

Create, deploy, and query a [Subgraph](/subgraphs/developing/developer-faq/#1-what-is-a-subgraph) on The Graph Network.

By the end, you'll have:

- Initialized a Subgraph from a smart contract
- Deployed it to Subgraph Studio for testing
- Published to The Graph Network for decentralized indexing

### Prerequisites

- A crypto wallet
- A deployed smart contract on a [supported network](/supported-networks/)
- [Node.js](https://nodejs.org/) & a package manager of your choice (`npm`, `yarn` or `pnpm`)

### How to Build a Subgraph

#### 1. Create a Subgraph in Subgraph Studio

1. Go to [Subgraph Studio](https://thegraph.com/studio/)
2. Connect your wallet
3. Click "Create a Subgraph"
4. Name it in Title Case: "Subgraph Name Chain Name"

#### 2. Install the Graph CLI

On your local machine, run one of the following commands:

Using [npm](https://www.npmjs.com/):

```sh
npm install -g @graphprotocol/graph-cli@latest
```

Using [yarn](https://yarnpkg.com/):

```sh
yarn global add @graphprotocol/graph-cli
```

Verify install:

```sh
graph --version
```

#### 3. Initialize your Subgraph

> You can find commands for your specific Subgraph in [Subgraph Studio](https://thegraph.com/studio/).

The following command initializes your Subgraph from an existing contract and indexes events:

```sh
graph init
```

When you initialize your Subgraph, the CLI will ask you for the following information:

- **Protocol**: Choose the protocol your Subgraph will be indexing data from.
- **Subgraph slug**: Create a name for your Subgraph. Your Subgraph slug is an identifier for your Subgraph.
- **Directory**: Choose a directory to create your Subgraph in.
- **Ethereum network** (optional): You may need to specify which EVM-compatible network your Subgraph will be indexing data from.
- **Contract address**: Locate the smart contract address you’d like to query data from.
- **ABI**: If the ABI is not auto-populated, you will need to input it manually as a JSON file.
- **Start Block**: You should input the start block where the contract was deployed to optimize Subgraph indexing of blockchain data.
- **Contract Name**: Input the name of your contract.
- **Index contract events as entities**: It is suggested that you set this to true, as it will automatically add mappings to your Subgraph for every emitted event.
- **Add another contract** (optional): You can add another contract.

#### 4. Edit your Subgraph

When making changes to the Subgraph, you will mainly work with three files:

- Manifest (`subgraph.yaml`) - defines what data sources your Subgraph will index.
- Schema (`schema.graphql`) - defines what data you wish to retrieve from the Subgraph.
- AssemblyScript Mappings (`mapping.ts`) - translates data from your data sources to the entities defined in the schema.

For a detailed breakdown on how to write your Subgraph, check out [Creating a Subgraph](https://thegraph.com/docs/en/subgraphs/developing/creating/starting-your-subgraph/).

#### 5. Deploy your Subgraph

When you **deploy** a Subgraph, you push it to [Subgraph Studio](https://thegraph.com/studio/), where you can test, stage and review it. A deployed Subgraph's indexing is performed by the [Upgrade Indexer](https://thegraph.com/blog/upgrade-indexer/), which is a single Indexer owned and operated by Edge & Node. A **deployed** Subgraph is free to use, rate-limited, not visible to the public, and meant to be used for development, staging, and testing purposes.

Once your Subgraph is written, run the following commands:

```sh
graph codegen && graph build
```

Authenticate and deploy your Subgraph. The deploy key can be found on the Subgraph's page in Subgraph Studio.

```sh

graph auth <DEPLOY_KEY>

graph deploy <SUBGRAPH_SLUG>
```

#### 6. Review your Subgraph

If you’d like to test your Subgraph before publishing it, you can use [Subgraph Studio](https://thegraph.com/studio/) to do the following:

- Run a sample query.
- Analyze your Subgraph in the dashboard to check information.
- Check the logs on the dashboard to see if there are any errors with your Subgraph.

#### 7. Publish your Subgraph to The Graph Network

When your Subgraph is ready for a production environment, you can publish it to the decentralized network. Publishing is an onchain action that does the following:

- It makes your Subgraph available to be to indexed by the decentralized [Indexers](https://thegraph.com/docs/en/indexing/overview/) on The Graph Network.
- It removes rate limits and makes your Subgraph publicly searchable and queryable in [Graph Explorer](https://thegraph.com/explorer/).
- It makes your Subgraph available for [Curators](https://thegraph.com/docs/en/resources/roles/curating/) to add curation signal.

To publish your Subgraph, click the Publish button in the dashboard and select your network.

> It is recommended that you curate your own Subgraph with at least 3,000 GRT to incentivize indexing.

To save on gas costs, you can curate your Subgraph in the same transaction when you publish.

#### 8. Query your Subgraph

You now have access to 100,000 free queries per month with your Subgraph on The Graph Network!

You can query your Subgraph by sending GraphQL queries to its Query URL, which you can find by clicking the Query button.

For more information about querying data from your Subgraph, read [Querying The Graph](https://thegraph.com/docs/en/subgraphs/querying/introduction/).

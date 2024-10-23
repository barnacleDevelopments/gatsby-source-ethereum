# gatsby-source-ethereum

A Gatsby plugin for sourcing data into your Gatsby application from an Ethereum node.

The plugin creates File nodes from on chain data.

## Install

`bash
npm install gatsby-source-filesystem
`

## How to use

You can have multiple instances of this plugin in your gatsby-config to read files from different nodes on other blockchains. Be sure to give each instance a unique name.
`javascript
module.exports = {
  plugins: [
    {
      resolve:`gatsby-source-ethereum`,
      options: {
      // The unique name for each instance
      name: `pages`,
      // Path to the directory
      path: `${__dirname}/src/pages/`,
      },
    },
  {
  resolve: `gatsby-source-filesystem`,
    options: {
      name: `data`,
      path: `${\_\_dirname}/src/data/`,
      // Ignore files starting with a dot
      ignore: [`\*_/\._`],
      // Use "mtime" and "inode" to fingerprint files (to check if file has changed)
      fastHash: true,
      },
    },
  ],
}
`
In the above example every file under src/pages and src/data will be made available as a File node inside GraphQL. You don't need to set up another instance of gatsby-source-filesystem for e.g. src/data/images (since those files are already sourced). However, if you want to be able to filter your files you can set up a new instance and later use the sourceInstanceName.

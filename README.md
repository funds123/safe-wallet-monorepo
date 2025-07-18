# <img src="https://github.com/user-attachments/assets/b8249113-d515-4c91-a12a-f134813614e8" height="60" valign="middle" alt="Safe{Wallet}" style="background: #fff; padding: 20px; margin: 0 -20px" />

# Safe{Wallet} monorepo

🌐 [Safe{Wallet} web app](/apps/web/README.md) ・ 📱 [Safe{Wallet} mobile app](/apps/mobile/README.md)

## Overview

Welcome to the Safe{Wallet} monorepo! This repository houses multiple applications and packages managed under a unified
structure using Yarn Workspaces. The monorepo setup simplifies dependency management and ensures consistent development
practices across projects.

### Key components

- **apps/**: Contains application projects (e.g., `mobile` for the Safe{Wallet} mobile app).
- **packages/**: Shared libraries and utilities.
- **config/**: Configuration files for the monorepo.

## Getting started

To get started, ensure you have the required tools installed and follow these steps:

### Prerequisites

- **Node.js**: Install the latest stable version from [Node.js](https://nodejs.org/).
- **Yarn**: Use Yarn version 4.5.3 or later

to install it with the latest node version you can simply do

```bash
corepack enable
```

and then just run

```bash
yarn
```

This will install the required version of yarn and resolve all dependencies.

> [!NOTE]
>
> Corepack is a tool to help with managing versions of your package managers. It exposes binary proxies for each supported package manager that, when called, will identify whatever package manager is
> configured for the current project, download it if needed, and finally run it.

### Initial setup

1. Clone the repository:

```bash
git clone <repo-url>
cd monorepo
```

2. Install dependencies:

```bash
yarn install
```

## Monorepo commands

Here are some essential commands to help you navigate the monorepo:

### Workspace management

- **Run a script in a specific workspace:**

```bash
yarn workspace <workspace-name> <script>
```

Example:

```bash
yarn workspace @safe-global/web start
```

- **Add a dependency to a specific workspace:**

```bash
yarn workspace <workspace-name> add <package-name>
```

- **Remove a dependency from a specific workspace:**

```bash
yarn workspace <workspace-name> remove <package-name>
```

> [!Note]
>
> Yarn treats commands that contain a colon as global commands. For example if you have a
> command in a workspace that has a colon and there isn't another workspace that has the same command,
> you can run the command without specifying the workspace name. For example:
>
> ```bash
> yarn cypress:open
> ```
>
> is equivalent to:
>
> ```bash
> yarn workspace @safe-global/web cypress:open
> ```

### Linting and formatting

- **Run ESLint across all workspaces:**

```bash
yarn lint
```

### Testing

- **Run unit tests across all workspaces:**

```bash
yarn test
```

## Contributing

### Adding a new workspace

1. Create a new directory under `apps/` or `packages/`.
2. Add a `package.json` file with the appropriate configuration.
3. Run:

```bash
yarn install
```

### Best practices

- Use Yarn Workspaces commands for managing dependencies.
- Ensure tests and linting pass before pushing changes.
- Follow the commit message guidelines.

### Tools & configurations

- **Husky**: Pre-commit hooks for linting and tests.
- **ESLint & Prettier**: Enforce coding standards and formatting.
- **Jest**: Unit testing framework.
- **Expo**: Mobile app framework for the `mobile` workspace.
- **Next.js**: React framework for the `web` workspace.

## Useful links

- [Yarn Workspaces Documentation](https://classic.yarnpkg.com/en/docs/workspaces/)
- [Expo Documentation](https://docs.expo.dev/)
- [Next.js Documentation](https://nextjs.org/docs)
- [Jest Documentation](https://jestjs.io/)
- [ESLint Documentation](https://eslint.org/)
- [Prettier Documentation](https://prettier.io/)

---

If you have any questions or run into issues, feel free to open a discussion or contact the maintainers. Happy coding!
🚀

# Safe Deployments

[![npm version](https://badge.fury.io/js/%40safe-global%2Fsafe-deployments.svg)](https://badge.fury.io/js/%40safe-global%2Fsafe-deployments)
[![CI](https://github.com/safe-global/safe-deployments/actions/workflows/test.yml/badge.svg)](https://github.com/safe-global/safe-deployments/actions/workflows/test.yml)

This contract contains a collection of deployments of the contract of the [Safe contracts repository](https://github.com/safe-global/safe-smart-account).

The addresses on the different networks and the abi files are available for each deployment. To get an overview of the available versions, check the available [json assets](./src/assets/).

## Adding additional deployments:

1. Follow the [deployment steps in the Safe contract repository](https://github.com/safe-global/safe-smart-account/#deployments).
2. Verify that the addresses match the expected address for each contract. You can find them under the "addresses" mapping in the respective JSON file in the [assets folder](./src/assets/).
3. Create a PR adding the new deployment. Example PR can be found [here](https://github.com/safe-global/safe-deployments/pull/676).

## Deployments overview

> ContractScan is a 3rd party tool that is not maintained by the Safe team

- [1.0.0](https://contractscan.xyz/bundle?name=Safe+1.0.0&addresses=0xb6029ea3b2c51d09a50b53ca8012feeb05bda35a,0x12302fe9c02ff50939baaaaf415fc226c078613c)
- [1.1.1](https://contractscan.xyz/bundle?name=Safe+1.1.1&addresses=0xf61a721642b0c0c8b334ba3763ba1326f53798c0,0x8538fcbccba7f5303d2c679fa5d7a629a8c9bf4a,0xd5d82b6addc9027b22dca772aa68d5d74cdbdf44,0x34cfac646f301356faa8b21e94227e3583fe3f5f,0x8d29be29923b68abfdd21e541b9374737b49cdad,0x76e2cfc1f5fa8f6a5b3fc4c8f4788f0116861f9b)
- [1.2.0](https://contractscan.xyz/bundle?name=Safe+1.2.0&addresses=0x6851d6fdfafd08c0295c392436245e5bc78b0185)
- 1.3.0
  - [Canonical](https://contractscan.xyz/bundle?name=Safe+1.3.0&addresses=0xf48f2b2d2a534e402487b3ee7c18c33aec0fe5e4,0x7cbb62eaa69f79e6873cd1ecb2392971036cfaa4,0xd9db270c1b5e3bd161e8c8503c55ceabee709552,0x3e5c63644e683549055b9be8653de26e0b4cd36e,0xa238cbeb142c10ef7ad8442c6d1f9e89e07e7761,0x40a2accbd92bca938b02010e17a5b8929b49130d,0xa6b71e26c5e0845f74c812102ca7114b6a896ab2,0xa65387f16b013cf2af4605ad8aa5ec25a2cba3a2,0x59ad6735bcd8152b84860cb256dd9e96b85f69da)
  - [EIP155](https://contractscan.xyz/bundle?name=Safe+1.3.0+EIP155&addresses=0x017062a1de2fe6b99be3d9d37841fed19f573804,0xb19d6ffc2182150f8eb585b79d4abcd7c5640a9d,0x69f4d1788e39c87893c980c06edf4b7f686e2938,0xfb1bffc9d739b8d520daf37df666da4c687191ea,0x998739bfdaadde7c933b942a68053933098f9eda,0xa1dabef33b3b82c7814b6d82a79e50f4ac44102b,0xc22834581ebc8527d974f8a1c97e1bea4ef910bc,0x98ffbbf51bb33a056b08ddf711f289936aaff717,0x727a77a074d1e6c4530e814f89e618a3298fc044)
  - [ZKsync](https://contractscan.xyz/bundle?name=Safe+1.3.0+ZKsync&addresses=0x2f870a80647bbc554f3a0ebd093f11b4d2a7492a,0xcb8e5e438c5c2b45fbe17b02ca9af91509a8ad56,0xb00ce5cccdef57e539ddced01df43a13855d9910,0x1727c2c531cf966f902e5927b98490fdfb3b2b70,0x0dfcccb95225ffb03c6fbb2559b530c2b7c8a912,0xf220d3b4dfb23c4ade8c88e526c1353abacbc38f,0xdaec33641865e4651fb43181c6db6f7232ee91c2,0x357147caf9c0cca67dfa0cf5369318d8193c8407,0x4191e2e12e8bc5002424ce0c51f9947b02675a44)
- [1.4.1](https://contractscan.xyz/bundle?name=Safe+1.4.1&addresses=0xfd0732dc9e303f09fcef3a7388ad10a83459ec99,0x9b35af71d77eaf8d7e40252370304687390a1a52,0x38869bf66a61cf6bdb996a6ae40d5853fd43b526,0x9641d764fc13c8b624c04430c7356c1c7c8102e2,0x41675c099f32341bf84bfc5382af534df5c7461a,0x29fcb43b46531bca003ddc8fcb67ffe91900c762,0x4e1dcf7ad4e460cfd30791ccc4f9c8a4f820ec67,0xd53cd0ab83d845ac265be939c57f53ad838012c9,0x3d4ba2e0884aa488718476ca2fb8efc291a46199,0x526643F69b81B008F46d95CD5ced5eC0edFFDaC6,0xfF83F6335d8930cBad1c0D439A841f01888D9f69,0xBD89A1CE4DDe368FFAB0eC35506eEcE0b1fFdc54)


## Install

- npm - `npm i @safe-global/safe-deployments`
- yarn - `yarn add @safe-global/safe-deployments`

## Usage

It is possible to directly use the JSON files in the [assets folder](./src/assets/) that contain the addresses and ABI definitions.

An alternative is using JavaScript library methods to query the correct deployment. The library supports different methods to get the deployment of a specific contract.

Each of the methods takes an optional `DeploymentFilter` as a parameter.

```ts
interface DeploymentFilter {
  version?: string;
  released?: boolean; // Defaults to true if no filter is specified
  network?: string; // Chain id of the network
}
```

### V1 Methods (single deployments)

Those methods will return a `SingletonDeployment` object or `undefined` if no deployment was found for the specified filter.

```ts
export interface SingletonDeployment {
  // The default address of the deployment.
  defaultAddress: string;

  // Indicates if the deployment is released.
  released: boolean;

  // The name of the contract.
  contractName: string;

  // The version of the deployment.
  version: string;

  // The address & hash of the contract code, where the key is the deployment type.
  // There could be multiple deployment types: canonical, eip155, zksync
  // Possible addresses per version:
  // 1.0.0: canonical
  // 1.1.1: canonical
  // 1.2.0: canonical
  // 1.3.0: canonical, eip155, zksync
  // 1.4.1: canonical, zksync
  // Ex: deployments: { "canonical": { "codeHash": "0x1234", "address": "0x5678"}}
  deployments: Record<string, { address: string; codeHash: string }>;

  // A record of network addresses, where the key is the network identifier and the value is the address.
  networkAddresses: Record<string, string>;

  // The ABI (Application Binary Interface) of the contract.
  abi: any[];
}
```

- Safe

```ts
const safeSingleton = getSafeSingletonDeployment();

// Returns latest contract version, even if not finally released yet
const safeSingletonNightly = getSafeSingletonDeployment({ released: undefined });

// Returns released contract version for specific network
const safeSingletonGÃ¶rli = getSafeSingletonDeployment({ network: '5' });

// Returns released contract version for specific version
const safeSingleton100 = getSafeSingletonDeployment({ version: '1.0.0' });

// Version with additional events used on L2 networks
const safeL2Singleton = getSafeL2SingletonDeployment();
```

- Factories

```ts
const proxyFactory = getProxyFactoryDeployment();
```

- Libraries

```ts
const multiSendLib = getMultiSendDeployment();

const multiSendCallOnlyLib = getMultiSendCallOnlyDeployment();

const createCallLib = getCreateCallDeployment();

const signMessageLib = getSignMessageLibDeployment();
```

- Handler

```ts

const callbackHandler = getDefaultCallbackHandlerDeployment();

const compatHandler = getCompatibilityFallbackHandlerDeployment();
```

### V2 Methods (multiple deployments)

We added a new methods that allow multiple deployment addresses for a contract.

Those methods will return a `SingletonDeployment` object or `undefined` if no deployment was found for the specified filter. Notice the difference in the `networkAddresses` field.

```ts
export interface SingletonDeployment {
  // The default address of the deployment.
  defaultAddress: string;

  // Indicates if the deployment is released.
  released: boolean;

  // The name of the contract.
  contractName: string;

  // The version of the deployment.
  version: string;

  // The address & hash of the contract code, where the key is the deployment type.
  // There could be multiple deployment types: canonical, eip155, zksync
  // Possible addresses per version:
  // 1.0.0: canonical
  // 1.1.1: canonical
  // 1.2.0: canonical
  // 1.3.0: canonical, eip155, zksync
  // 1.4.1: canonical, zksync
  // Ex: deployments: { "canonical": { "codeHash": "0x1234", "address": "0x5678"}}
  deployments: Record<string, { address: string; codeHash: string }>;

  // A record of network addresses, where the key is the network identifier and the value is the address.
  networkAddresses: Record<string, string | string[]>;

  // The ABI (Application Binary Interface) of the contract.
  abi: any[];
}
```

- Safe

```ts
const safeSingleton = getSafeSingletonDeployments();

// Returns latest contract version, even if not finally released yet
const safeSingletonNightly = getSafeSingletonDeployments({ released: undefined });

// Returns released contract version for specific network
const safeSingletonGÃ¶rli = getSafeSingletonDeployments({ network: '5' });

// Returns released contract version for specific version
const safeSingleton100 = getSafeSingletonDeployments({ version: '1.0.0' });

// Version with additional events used on L2 networks
const safeL2Singleton = getSafeL2SingletonDeployments();
```

- Factories

```ts
const proxyFactory = getProxyFactoryDeployments();
```

- Libraries

```ts
const multiSendLib = getMultiSendDeployments();

const multiSendCallOnlyLib = getMultiSendCallOnlyDeployments();

const createCallLib = getCreateCallDeployments();

const signMessageLib = getSignMessageLibDeployments();
```

- Handler

```ts

const callbackHandler = getDefaultCallbackHandlerDeployments();

const compatHandler = getCompatibilityFallbackHandlerDeployments();
```

## Release cycle

`safe-deployments` release cycle is once per month, except for urgent issues that require immediate attention.

## Notes

- v1 supports only one address per network, while v2 allows multiple addresses per network. To maintain compatibility with v1, the address order in v2 is arranged so that the first address matches the one used in v1.

- A list of network information can be found at [chainid.network](https://chainid.network/)

## License

This library is released under MIT.

"deploying "SimulateTxAccessor" (tx: 0x0d49991b464494a7d6dda930509e10e3047bde27fb16ff373016e76d39df56b0)... : deployed at 0x3d4BA2E0884aa488718476ca2FB8Efc291A46199 with 237931 gas deploying "SafeProxyFactory" (tx: 0xd5463a634a5e7e4a42a69f4b4ec4bb14ee4525b3eec56967f527a0b93e999642)...: deployed at 0x4e1DCf7AD4e460CfD30791CCC4F9c8a4f820ec67 with 712622 gas deploying "TokenCallbackHandler" (tx: 0xc7616c04deb1dccf7a903ae6edc00d578c3b0dce380e1717461c1f1d88069052)...: deployed at 0xeDCF620325E82e3B9836eaaeFdc4283E99Dd7562 with 453406 gas deploying "CompatibilityFallbackHandler" (tx: 7)...: deployed at 0xfd0732Dc9E303f09fCEf3a7388Ad10A83459Ec99 with 1270132 gas deploying "CreateCall" (tx: 0xc3c9c4739729d806afee4b4d2b1f6dea248fe311417bfbf36906f5a2a7cabf5e)...: deployed at 0x9b35Af71d77eaf8d7e40252370304687390A1A52 with 290470 gas deploying "MultiSend" (tx: 0x44c1bc5541afc8f4c1df1d192e1ba2bd42fbceb73ced59582dfbc5c18220f67b)...: deployed at 0x38869bf66a61cF6bDB996A6aE40D5853Fd43B526 with 190062 gas deploying "MultiSendCallOnly" (tx: 0x147e48f9092114f14af96eff5428e0dfa62336f6ad2a02485d10df80311886e4)...: deployed at 0x9641d764fc13c8B624c04430C7356C1C7C8102e2 with 142150 gas deploying "SignMessageLib" (tx: 0xd79b91f0af84cc0120b7332cb0c8422cbadc7db2cb4607329443f1324a2ffe28)...: deployed at 0xd53cd0aB83D845Ac265BE939c57F53AD838012c9 with 262417 gas deploying "SafeToL2Setup" (tx: 0x6c5ca4c7cc525a4aaf9bf94cf4723799b43424ca5f1ff48c69ee4ebb62385ab7)...: deployed at 0xBD89A1CE4DDe368FFAB0eC35506eEcE0b1fFdc54 with 230863 gas deploying "Safe" (tx: 0x8ce9463df880f03ff5b8288c340ea4ca58c73350d30f6f1b6fa7af24b9ca9e0b)...: deployed at 0x41675C099F32341bf84BFc5382aF534df5C7461a with 5150072 gas deploying "SafeL2" (tx: 0x453c3b63fcf4b6d62a92e8c95aea6c912a807bfb41177612267b38af8287a500)...: deployed at 0x29fcB43b46531BcA003ddC8FCB67FFE91900C762 with 5332531 gas deploying "SafeToL2Migration" (tx: 0xcc8b7981b88d9e918bfcac5edb89bdd958ace054ed804d76eb71ee1cb32a72b4)...: deployed at 0xfF83F6335d8930cBad1c0D439A841f01888D9f69 with 1283078 gas deploying "SafeMigration" (tx: 0x47ce1211deff300043e320201b4a51497a8c42e1825fe17425d42d4c96588267)...: deployed at 0x526643F69b81B008F46d95CD5ced5eC0edFFDaC6 with 512858 gas

You can view, comment on, or merge this pull request online at:
  https://github.com/safe-global/safe-deployments/pull/1140

Commit Summary
5513bd1 feat(plasma-testnet-1.4.1): added plasma testnet 1.4.1
File Changes (12 files)
M src/assets/v1.4.1/compatibility_fallback_handler.json (1)
M src/assets/v1.4.1/create_call.json (1)
M src/assets/v1.4.1/multi_send.json (1)
M src/assets/v1.4.1/multi_send_call_only.json (1)
M src/assets/v1.4.1/safe.json (1)
M src/assets/v1.4.1/safe_l2.json (1)
M src/assets/v1.4.1/safe_migration.json (1)
M src/assets/v1.4.1/safe_proxy_factory.json (1)
M src/assets/v1.4.1/safe_to_l2_migration.json (1)
M src/assets/v1.4.1/safe_to_l2_setup.json (1)
M src/assets/v1.4.1/sign_message_lib.json (1)
M src/assets/v1.4.1/simulate_tx_accessor.json (1)
Patch Links:
https://github.com/safe-global/safe-deployments/pull/1140.patch
https://github.com/safe-global/safe-deployments/pull/1140.diff


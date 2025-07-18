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
,"Here’s a refreshed template for your ethereum_wallet_view_safe_app, following the latest trends and improvements inspired by modern wallets like Gnosis Safe Wallet:


---

🛠️ 1. Upgrade Dependencies & Architecture

Migrate to safe-wallet-web@v1.44.x, the latest release as of late 2024 with enhanced EIP‑712 support, better gas estimation, and improved Safe App handling  .

Use Modular UI stacks (React/TypeScript or Vue) mirroring Web3‑Wallet modular design—a flexible core, with separate connectors and UI components  .



---

📁 2. Project Structure

/src/
  /connectors/        // wallet connectors (MetaMask, WalletConnect, Safe)
  /utils/             // web3 helpers, formatters, EIP‑155, EIP‑712
  /components/
    Header.tsx
    BalanceView.tsx
    TxHistoryList.tsx
    SafeAppHandler.tsx
  /views/
    Dashboard.tsx
    SendTokens.tsx
  App.tsx
  index.tsx
  safeConfig.ts       // Safe config


---

⚙️ 3. Core Connection Logic – Example (TypeScript + React):

import { SafeAppProvider, getSafeApiKit } from '@safe-global/safe-apps-provider';
import Safe, { SafeFactory, EthersAdapter } from '@safe-global/safe-core-sdk';
import { ethers } from 'ethers';

export async function initSafe() {
  const provider = new ethers.providers.Web3Provider((window as any).ethereum);
  const ethAdapter = new EthersAdapter({ ethers, signer: provider.getSigner() });
  const safeFactory = await SafeFactory.create({ ethAdapter });
  // Example: instantiate or connect to a known Safe
  const safeAddress = await Safe.create({ ethAdapter, safeAccountConfig: { owners: [await provider.getSigner().getAddress()], threshold: 1 } });
  return safeAddress;
}

export function SafeAppHandler() {
  const [safeInfo, setSafeInfo] = useState(null);
  useEffect(() => {
    const appProvider = new SafeAppProvider(window.ethereum, window.location.origin);
    const sdk = getSafeApiKit({ ethAdapter: appProvider.ethAdapter, safeAddress: appProvider.safeAddress });
    sdk.getSafeInfo().then(setSafeInfo);
  }, []);
  // UI render
}


---

💰 4. Display Balance & Historical Transactions

Utilize provider methods or Safe API SDK to fetch:

const balances = await sdk.getTokenBalances();        // Safe-specific assets
const history = await sdk.getTransactions({ limit: 20 });

Render them with your BalanceView and TxHistoryList components.


---

📦 5. Sending Transactions via Safe

Example pattern—creating & submitting transactions instead of raw transfers (for multisig flow):

async function sendTx(to: string, valueWei: string, data = '0x') {
  const safeSdk = await Safe.create({ ethAdapter, safeAddress });
  const safeTransaction = await safeSdk.createTransaction({ to, data, value: valueWei });
  const txResponse = await safeSdk.executeTransaction(safeTransaction);
  await txResponse.transactionResponse?.wait();
}


---

📱 6. Safe App Integration

Ensure full compatibility with Safe app ecosystem:

Handle URL message signing & transaction requests using SafeAppProvider.

Support EIP‑712. Version 1.44+ includes typed-data support  .

Use separate UI elements/messages like “Open in Safe” if not accessed inside a Safe context.



---

🎨 7. UI/UX Suggestions

Modern token view: fetch token logos via Coingecko/web3 or local SVG assets.

Gas & fee estimates: Use estimateGas and show fees to users upfront.

Themeable UI: Dark/light mode via CSS variables or Tailwind themes.

Error handling: Global error boundary for RPC/network issues.



---

✅ Checklist Summary

Task	Status

Upgrade to safe-wallet-web latest version	🔲
Modular connector architecture	🔲
Wallet & Safe init	🔲
Balance fetch & rendering	🔲
Transaction history	🔲
EIP‑712 signing support	🔲
UX polish: gas, theme, logos	🔲



---

🚀 Next Steps

1. Update your package.json with the latest @safe-global/* dependencies.


2. Refactor your connection & UI layers using the new modular structure.


3. Deploy a prototype and test inside a Safe.


4. Iterate on UI/UX: improved experiences for token display, errors, themes.



If you’d like, I can generate some code snippets or scaffold App.tsx & BalanceView.tsx files across React/TS or Vue—just let me know your preferred stack!

Here’s a refreshed template for your ethereum_wallet_view_safe_app, following the latest trends and improvements inspired by modern wallets like Gnosis Safe Wallet:


---

🛠️ 1. Upgrade Dependencies & Architecture

Migrate to safe-wallet-web@v1.44.x, the latest release as of late 2024 with enhanced EIP‑712 support, better gas estimation, and improved Safe App handling  .

Use Modular UI stacks (React/TypeScript or Vue) mirroring Web3‑Wallet modular design—a flexible core, with separate connectors and UI components  .



---

📁 2. Project Structure

/src/
  /connectors/        // wallet connectors (MetaMask, WalletConnect, Safe)
  /utils/             // web3 helpers, formatters, EIP‑155, EIP‑712
  /components/
    Header.tsx
    BalanceView.tsx
    TxHistoryList.tsx
    SafeAppHandler.tsx
  /views/
    Dashboard.tsx
    SendTokens.tsx
  App.tsx
  index.tsx
  safeConfig.ts       // Safe config


---

⚙️ 3. Core Connection Logic – Example (TypeScript + React):

import { SafeAppProvider, getSafeApiKit } from '@safe-global/safe-apps-provider';
import Safe, { SafeFactory, EthersAdapter } from '@safe-global/safe-core-sdk';
import { ethers } from 'ethers';

export async function initSafe() {
  const provider = new ethers.providers.Web3Provider((window as any).ethereum);
  const ethAdapter = new EthersAdapter({ ethers, signer: provider.getSigner() });
  const safeFactory = await SafeFactory.create({ ethAdapter });
  // Example: instantiate or connect to a known Safe
  const safeAddress = await Safe.create({ ethAdapter, safeAccountConfig: { owners: [await provider.getSigner().getAddress()], threshold: 1 } });
  return safeAddress;
}

export function SafeAppHandler() {
  const [safeInfo, setSafeInfo] = useState(null);
  useEffect(() => {
    const appProvider = new SafeAppProvider(window.ethereum, window.location.origin);
    const sdk = getSafeApiKit({ ethAdapter: appProvider.ethAdapter, safeAddress: appProvider.safeAddress });
    sdk.getSafeInfo().then(setSafeInfo);
  }, []);
  // UI render
}


---

💰 4. Display Balance & Historical Transactions

Utilize provider methods or Safe API SDK to fetch:

const balances = await sdk.getTokenBalances();        // Safe-specific assets
const history = await sdk.getTransactions({ limit: 20 });

Render them with your BalanceView and TxHistoryList components.


---

📦 5. Sending Transactions via Safe

Example pattern—creating & submitting transactions instead of raw transfers (for multisig flow):

async function sendTx(to: string, valueWei: string, data = '0x') {
  const safeSdk = await Safe.create({ ethAdapter, safeAddress });
  const safeTransaction = await safeSdk.createTransaction({ to, data, value: valueWei });
  const txResponse = await safeSdk.executeTransaction(safeTransaction);
  await txResponse.transactionResponse?.wait();
}


---

📱 6. Safe App Integration

Ensure full compatibility with Safe app ecosystem:

Handle URL message signing & transaction requests using SafeAppProvider.

Support EIP‑712. Version 1.44+ includes typed-data support  .

Use separate UI elements/messages like “Open in Safe” if not accessed inside a Safe context.



---

🎨 7. UI/UX Suggestions

Modern token view: fetch token logos via Coingecko/web3 or local SVG assets.

Gas & fee estimates: Use estimateGas and show fees to users upfront.

Themeable UI: Dark/light mode via CSS variables or Tailwind themes.

Error handling: Global error boundary for RPC/network issues.



---

✅ Checklist Summary

Task	Status

Upgrade to safe-wallet-web latest version	🔲
Modular connector architecture	🔲
Wallet & Safe init	🔲
Balance fetch & rendering	🔲
Transaction history	🔲
EIP‑712 signing support	🔲
UX polish: gas, theme, logos	🔲



---

🚀 Next Steps

1. Update your package.json with the latest @safe-global/* dependencies.


2. Refactor your connection & UI layers using the new modular structure.


3. Deploy a prototype and test inside a Safe.


4. Iterate on UI/UX: improved experiences for token display, errors, themes.



If you’d like, I can generate some code snippets or scaffold App.tsx & BalanceView.tsx files across React/TS or Vue—just let me know your preferred stack!



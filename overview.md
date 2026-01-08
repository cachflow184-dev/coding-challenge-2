# Overview
In this file I report my finding about this project

## Project structure assessment
The project is compose about three main components: Contracts, Server, and Frontend, but everything is mixed up in a gigantic application without boundaries between each component. 

### Contracts
The contracts component is composed by two folders: `contracts` and `migrations`, with the truffle configuration files. They should be moved in a shared folder.

### Server
The server has its own `package.json` file, and the files are organized by use (`config`, `models`, and `routes`), but they should stick to a common naming convention.

### Frontend
The Frontend code oraganization is poor, and there are stuff in the wrong place. For example, the `fonts` folder should be under `assets`, the `reducer.js` should be in the `reducers` folder and named `index.js`, the code is not split in features, so the `shared` folder should not exist, and all the components defined there should be moved under the `components` folder. 
There is no naming convention: some files use the Pascal naming (e.g. `BlockExplorer`), other use the Camel Case (e.g. `userReducer`), some uses a lowercase naming (e.g. `loginbutton`), and finally there are other using Kebab naming convention (e.g. `puse-min.css`). You should stick to a naming convention.

## Timeline and dependency analysis

### Contracts
It uses solidity version 0.4.2, that is very old (it was released in 2016, while the latest release is 0.8.32). Using a so old solidity version expose the smart contract to a lot of vulnerabilities, and it doesn't include the latest features introduced in the blockchain. Futhermore, it can not be compatible with the latest etherium libraries.

### Server
There are a few outdated dependencies, like `express-jwt` (installed `3.3.0`, latest `8.5.1`), mongoose (installed `4.4.10`, latest: `9.1.2`), and so on. Using old package version exposes to possible vulnerability attacks: `npm audit` finds 83 vulnerabilities (4 low, 21 moderate, 43 high, 15 critical). 
It's written in Javascript, while Typescript should be adopted to reduce errors.

### Frontend
The frontend package includes old libraries with 287 vulnerabilities (14 low, 82 moderate, 91 high, 100 critical). Furthermore, it uses old-fashioned libraries like `redux` and `web3`: the risk is to find bugs nobody fixes.
It's written in Javascript, while Typescript should be adopted to reduce errors.

## Potential execution risks
There are a lot of risk while deploying this application, mainly related to this topics:
- No code separation: a project like this is hard to maintain, because there is no clear separation of components and concern;
- Vulnerabilities: an hacker may break our code using a know vulnerabilities;
- Old-fashioned libraries: this increase the risk a bug cannot be fixed because there is no maintainer, or the mantainer is focused on other libraries;
- No tests: a good test suite is fondamental to reduce the risks of bugs, especially for edge cases that are difficult to test. Furthermore, a test suite helps in code refactor

## Recommendations for project management
When I lead a team, I try to build a common culture: I think people follows rules when they understand while a rule exists instead of enforcing it.

Even more important, creating a sense of belonging toward the product helps a lot to increase the quality of the work: I put much more passion in something that I use or own, instead of something that I don't fell like mine.

In an ideal team, every member can replace each other, but in practise, everybody is unique, and understanding it is crucial. In particular, there are people who just stick to the assigned task, and other who spend time reasearching and optimizing the product. Usually, the second kind are better for critical tasks.

Lastly, I believe in the leadership by doing: I cannot pretend a team member to spend hours on an annoying task, if I'm the first to avoid it. Usually, I do chores, and then the other members of the team understand I have more important things to do, and so they jump in or help out with a better approach.
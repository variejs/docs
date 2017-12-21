# Contracts

- [Why Use a Contract?](#why-use-a-contract?)

Varie's contracts are a set of interfaces that define the services of the framework. Each contract has a implementation which is set in the service providers of the framework.

## Why Use a Contract?

Varie uses contracts to provide loose coupling and to provide a sense of what a contract does. For instance Varie uses Vuex , but lets say you want to switch out Vuex for another state management system. This could cause problems for your application as you would have specific calls for Vuex it self. Instead we now can just switch out the implementation for for the same contract and would't have to change a single line of application code.

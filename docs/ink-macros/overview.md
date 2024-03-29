---
title: Overview
slug: /ink-macros-attributes
---

## ink! Macros & Attributes

### Entry Point

In a module annotated with `#[ink::contract]` these attributes are available:

| Attribute | Where Applicable | Description |
|:--|:--|:--|
| `#[ink(storage)]` | On `struct` definitions. | Defines the ink! storage struct. There can only be one ink! storage definition per contract. |
| `#[ink(event)]` | On `struct` definitions. | Defines an ink! event. A contract can define multiple such ink! events. |
| `#[ink(anonymous)]` | Applicable to ink! events. | Tells the ink! codegen to treat the ink! event as anonymous which omits the event signature as topic upon emitting. Very similar to anonymous events in Solidity. |
| `#[ink(topic)]` | Applicate on ink! event field. | Tells the ink! codegen to provide a topic hash for the given field. Every ink! event can only have a limited number of such topic field. Similar semantics as to indexed event arguments in Solidity. |
| `#[ink(message)]` | Applicable to methods. | Flags a method for the ink! storage struct as message making it available to the API for calling the contract. |
| `#[ink(constructor)]` | Applicable to method. | Flags a method for the ink! storage struct as constructor making it available to the API for instantiating the contract. |
| `#[ink(payable)]` | Applicable to ink! messages. | Allows receiving value as part of the call of the ink! message. ink! constructors are implicitly payable. |
| `#[ink(selector = "..")]` | Applicable to ink! messages and ink! constructors. | Specifies a concrete dispatch selector for the flagged entity. This allows a contract author to precisely control the selectors of their APIs making it possible to rename their API without breakage. |
| `#[ink(namespace = "..")]` | Applicable to ink! trait implementation blocks. | Changes the resulting selectors of all the ink! messages and ink! constructors within the trait implementation. Allows to disambiguate between trait implementations with overlapping message or constructor names. Use only with great care and consideration! |
| `#[ink(implementation)]` | Applicable to ink! implementation blocks. | Tells the ink! codegen that some implementation block shall be granted access to ink! internals even without it containing any ink! messages or ink! constructors. |

See [here](https://paritytech.github.io/ink/ink_lang/attr.contract.html) for a more detailed description of those and also for details on the `#[ink::contract]` macro.

### Trait Definitions

Use`#[ink::trait_definition]` to define your very own trait definitions that are then implementable by ink! smart contracts.
See e.g. the [`examples/trait-erc20`](https://github.com/paritytech/ink/blob/master/examples/trait-erc20/lib.rs#L49-L51) contract on how to utilize it or [the documentation](https://paritytech.github.io/ink/ink_lang/attr.trait_definition.html) for details.

### Off-chain Testing

The `#[ink::test]` proc. macro enables off-chain testing. See e.g. the [`examples/erc20`](https://github.com/paritytech/ink/blob/master/examples/erc20/lib.rs#L278-L280) contract on how to utilize those or [the documentation](https://paritytech.github.io/ink/ink_lang/attr.test.html) for details.


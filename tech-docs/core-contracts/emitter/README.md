## Overview

The emitter contract is responsible for:

Designating and modifying the protocol's backstop contract: this is set on Emitter initialization and can later be changed throw an emission fork(link).

Distributing Blend to the backstop contract and to drop(link) recipients.

Typically user's will not directly interact with the emitter contract.

Interface Docs: https://docs.rs/blend-interfaces/0.0.1/blend_interfaces/emitter/index.html
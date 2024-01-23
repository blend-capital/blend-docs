## Overview

The emitter is the admin of the Blend token and is responsible for minting and emitting Blend to the current backstop.

### Normal Emissions

Regular emissions are carried out via the `distribute` emitter function. This function mints an amount of Blend equal to the number of seconds that have passed since the last distribution time and sends it to the backstop contract. The backstop contract handles further distribution logic.

### Drop Emissions

Blend emissions are also carried out via "Drops" these are fixed 50 million token emissions that can be carried out after every backstop swap. Only the current backstop contract can call the `drop` function which executes this emission, and each backstop contract can only call the function once. When the `drop` function is called the emitter contract uses a `drop_recipient` list stored in the backstop module contract to determine what addressed Blend should be minted to.

Drops are intended to incentivize further open source development of the protocol - as a backstop swap represents the release of a new protocol version.

# VRWorlds-Emissary-Rust
Rust Base for a WebAssembly VRWorlds Emissary (browser-side code)

## Emissary
The emissary is the name I've given to the browser side code which runs in a sandbox within the browser environment to give logic
and programability to 3d objects, and eventually serverside as well for the various types of servers.

These basically are webassembly modules.   Since it seems that Rust is the best webassembly language for now, this is where I'm going to 
start (not a language I know yet).   The basic idea is that they call a method in their main which provides an extensive filled out
protobuf buffer to the sandbox.   This call also provides a series of potential callbacks to the sandbox environment.   Implementation 
will depend on how WasmTime handles things after main returns.   I can't really have it tearing down the environment.   It may be that
the registration call just doesn't return.   Similarly I may have to leave it in some kind of light thread so it can just sleep--not 
sure yet if that thread would call the callbacks.   If main doesn't tear down the environment, I can just let that thread go.

I'd really love to be able to run directly in the browser in Unity, but I can't call .NET standard 2.1 yet (I don't think).   Latest
Unity also doesn't seem to support Steam VR anymore (there would be a new version of that sometime, but not sure it's out yet).  So, I 
have to do the multi-process stuff.

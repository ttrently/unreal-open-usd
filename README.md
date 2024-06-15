## Unreal Open USD

This repository contains an Unreal content plugin (`OpenUSDGames`) that demonstrates USD content building in Unreal.

	- primal_cube
	
## Notes

A collection of notes on the Unreal USD asset process.

### Importing

- Reimporting a USD asset through the content browser uses the first imported USD asset during the editor session. This can reproduce as:
	1. Import a.usd
	2. Import b.usd
	3. Reimport b.uasset from the content browser.
	4. Reimport window shows contents from a.usd instead of b.usd.
	
- UAssets need to be manually reimported into Unreal.
	- Possible option to have automatic caching / update mechanism similar to mesh builds?
- Edits made to the UAsset in Unreal need to be manually exported back into the source USD file.

### Materials

- Unreal material assignment can be done through the USD Stage View but can't be assigned from DCC (Maya, 3DSMax, etc.).
- Materials can be assigned in Unreal via the USD Stage View but only as a manually input string.
- Materials are bound via a `custom string unrealMaterial = "/Game/foo"` line. 
- MaterialX workflows seem hindered by having the custom string attribute for both import and export, needs to be cleaner.

### Collision

- `PhysicsCollisionAPI` and `PhysicsMeshCollisionAPI` can't be assigned from DCC.
- `PhysicsCollisionAPI` and `PhysicsMeshCollisionAPI` can be assigned through the USD Stage View, but not normal to user workflows.

### LOD's

- LOD's can be created from DCC but must have a specific prim structure.
- No control on LOD switch distances or custom vs generated.
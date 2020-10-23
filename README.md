# Better Foliage

### Summary

Better Foliage is a mod that will make your Minecraft worlds more impressive, mainly by improving how vegetation looks. 

This is port for Minecraft Bedrock Edition, working under Inner Core for Horizon. At the current moment this is alpha version, that contains only core features of the original mod.

### Adding Custom Leaves

To integrate better foliage with your mod, you need 2 things: generate leaves textures and setup render for leaves block.

To make preloader generate leaves textures, create file with extension .rescfg in your resources and add all leaves textures: 

```
{
    "better-foliage": {
        "leaves": [
            {"texture": "terrain-atlas/texture1.png"},
            ...
        ]
    }
}
```

Next, use follwing code to register render for leaves block:

```
ModAPI.addAPICallback("BetterFoliageLeaves", function(BetterFoliage) {
	BetterFoliage.setupLeavesModel(block id, data or -1, ["block texture name", block texture index]);
});
```

If your leaves use vanilla leaves color source, you may pass additional parameter, that specifies vanilla leaves type to get color from:

```
ModAPI.addAPICallback("BetterFoliageLeaves", function(BetterFoliage) {
	// vanilla leaves data:
	// 0 - oak
	// 1 - spruce 
	// 2 - birch
	// 3 - jungle
	BetterFoliage.setupLeavesModel(block id, data or -1, ["block texture name", block texture index], vanilla leaves data);
});
```

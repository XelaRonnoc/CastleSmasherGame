# Destructible Materials Properties and Creation:

## Brick

### Fracture Method:

-   Level 1: Blocks/Bricks
    -   Wall is sliced vertically to split the walls depth into the number of bricks desired
    -   Wall is sliced horizontally number of brick courses desired
    -   The resulting long bones can then be unevenly cut into bricks of similar but differing lengths so no two adjacent courses have exactly the same number or length of bricks. This is to emulate how real world bricks are not laid out directly upon one another and are instead staggered.
    -   All of the above fracture levels were flattened into one level so that the initial two slices created do not fracture more readily than the joins between adjacent bricks.
-   Level 2: Fragments
    -   A uniform Voronoi fracture is utilized to split the bricks into chunks
    -   This Voronoi fracture utilized a small amount of additional noise to create a roughness to these fractures to prevent a slate or obsidian like smooth fracture.
    -   The noise setting was:
        -   Amplitude = 4
        -   Lacunarity = 3
        -   Point Spacing = 8
    -   Breakpoint:
        -   Standard
            -   Level 1 = 500000.0
            -   Level 2 = 100000.0
        -   Thin
            -   Level 1 = 1000.0
            -   Level 2 = 5000.0

### Physics Material:

-   Friction = 0.7
    -   Static = 0.8
-   Restitution = 0.1
-   Density = 1.9g/cm^3
-   Raise Mass to Power = 0.9
-   Strength
    -   Tensile = 25.0 MPA
    -   Compression = 50.0 MPA
    -   Shear = 114.0 MPA \*This is likley too high and should be reduced
-   Damage Modifier multiplier = 1.0

## Concrete

### Fracture Method:

-   Level 1: Flattened Voronoi Fracture
    -   Create a uniform Voronoi fracture with a relatively small number of large pieces utilizing the noise settings below, repeat this 3 times doubling Voronoi sites each time, until you have approximately 1000 bones(dependent on wall size and desired level of detail).
    -   Flatten all levels created into one level
    -   The noise setting was:
        -   Amplitude = 4
        -   Lacunarity = 3
        -   Point Spacing = 8
-   Breakpoint:
    -   Standard
        -   Level 1 = 800000.0
    -   Thin
        -   Level 1 = 100000.0

### Physics Material:

-   Friction = 0.7
    -   Static = 0.8
-   Restitution = 0.1
-   Density = 2.4g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 2.4 MPA
    -   Compression = 24.0 MPA
    -   Shear = 2.0 MPA
-   Damage Modifier multiplier = 1.0

## Wood

### Fracture Method:

-   Level 1 Planks:
    -   Utilizing a uniform vertical grid slice separate the wall into the number of planks required, thicker walls may require more than one plank deep
    -   Around 16 planks is optimal but you may have to exceed this with bigger walls
-   Level 2 Grain Fracture:
    -   Utilizing the same slice fracture as above (although multiply by 2-3 times number of planks) fracture again with the below noise values
    -   The noise setting for grain fractures varied but in general was:
        -   Amplitude > 50
        -   Point Spacing > 50
        -   This will create long uneven cracks that run along the “grain”
-   Level 3 Splinter Fracture (gets flattened into level 2):
    -   Utilizing the slice functionality but horizontally instead of vertically
    -   Add between 3 and 8 slices with variability at between 10 and 20 to avoid creating straight lines and utilize below noise settings (ensure on deep walls if using variability, either fracture each row of planks like this individually with separate break lines or do them all at once across the same break line, adding additionally break lines for slices in the depth direction with all rows selected whilst adding noise and variability will result in weird sideways splinters between planks.)
    -   The noise setting for splinters was:
        -   Amplitude = 35
        -   Point Spacing = 2
    -   These were then further sharpened utilizing the normalization tool at a setting of 15
-   Breakpoint:
    -   Standard
        -   Level 1 = 300000.0
        -   Level 2 = 50000.0
    -   Thin
        -   Level 1 = 300000.0
        -   Level 2 = 50000.0

### Physics Material:

-   Friction = 0.7
    -   Static = 0.8
-   Restitution = 0.4
-   Density = 0.7g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 5.5 MPA
    -   Compression = 8.6 MPA
    -   Shear = 12.3 MPA
-   Damage Modifier multiplier = 1.0

## General

-   After a fracture is created remove tiny geo to reduce weird buggy breaks and reduce processor requirements
-   Ensure “Always create physics state” is checked to improve first impact performance
-   CCD and MACD can improve high velocity collision detection but can result in strange destructibility behavior on low velocity impacts
-   Ensure break damage and shock damage propagation are not set to 0. Having them set to 0 seems to cause more propagation that 0.1 or even 1
-   Ensure “Density from physics material” is checked
-   Ensure “Use material damage modifiers” is checked
-   Projectile Properties and Creation:

# Projectile Properties and Creation:

## Rock

### Push force magnitude = 2000

### Fracture Method:

-   Level 1 Standard Voronoi
-   Level 2 Standard Voronoi
-   Level 3 Standard Voronoi
-   Breakpoints
    -   Level 1 = 500000.0
    -   Level 2 = 50000.0
    -   Level 3 = 5000.0

### Physics Material:

-   Friction = 0.4
    -   Static = 0.5
-   Restitution = 0.3
-   Density = 7.85g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 450.0 MPA
    -   Compression = 900.0 MPA
    -   Shear = 250.0 MPA
-   Damage Modifier multiplier = 1.0

## Impact Explosive

### Push force magnitude = 2000

### Fracture Method:

-   Level 1 Standard Voronoi
-   Breakpoints
    -   Level 1 = 500000.0

### Physics Material:

-   Friction = 0.7
    -   Static = 0.8
-   Restitution = 0.01
-   Density = 2.65g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 12.0 MPA
    -   Compression = 210.0 MPA
    -   Shear = 1.0 MPA
-   Damage Modifier multiplier = 1.0

### Other:

-   Turn on CCD and MACD to improve collision detection

### Blueprint:

<div>
    <img src="Images/ImpactExplosiveBlueprint.png" alt="Impact Explosive Blueprint" width="3000"/>
</div>

## Timed Explosive

### Push force magnitude = 1500

### Fracture Method:

-   Level 1 Standard Voronoi
-   Level 2 Standard Voronoi
-   Level 3 Standard Voronoi
-   Breakpoints
    -   Level 1 = 500000.0
    -   Level 2 = 50000.0
    -   Level 3 = 5000.0

### Physics Material:

-   Friction = 0.7
    -   Static = 0.8
-   Restitution = 0.01
-   Density = 2.65g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 12.0 MPA
    -   Compression = 210.0 MPA
    -   Shear = 1.0 MPA
-   Damage Modifier multiplier = 1.0

### Blueprint

<div>
    <img src="Images/TimedExplosiveBlueprint.png" alt="Timed Explosive Blueprint" width="3000"/>
</div>

## Cannon Ball

### Push force magnitude = 6000

### Fracture Method:

-   Chaos but no fracture

### Physics Material:

-   Friction = 0.4
    -   Static = 0.5
-   Restitution = 0.001
-   Density = 19.28g/cm^3
-   Raise Mass to Power = 1.0
-   Strength
    -   Tensile = 2100.0 MPA
    -   Compression = 2000.0 MPA
    -   Shear = 400.0 MPA
-   Damage Modifier multiplier = 1.0

### Other:

-   Turn on CCD and MACD to improve collision detection

## General:

-   After a fracture is created remove tiny geo to reduce weird buggy breaks and reduce process requirements
-   Ensure “Always create physics state” is checked to improve first impact performance
-   Ensure “Density from physics material” is checked
-   Ensure “Use material damage modifiers” is checked

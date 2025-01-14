# COMP3180 Final Project Timeline/Diary

Alex Milton: 47159375

## Learning Goals and Metrics

#### Learning Goal 1:

Create high simulation fidelity physics based destruction simulations utilizing UE5 chaos destruction. This can be assessed against the below indicators:

-   Create interactions between projectile and destructible material. This may also include one or more of the below specific interactions:
    -   Overpenetration ✅
    -   Projectile fragmentation ✅
    -   Projectile deformation ❌
    -   Spalling ✅
-   Create interactions between destroyed or destructible materials and other destroyed or destructible materials. ✅

#### Learning Goal 2:

Utilize UE5 Chaos destruction in order to reduce the “Lego-Brick” look of destruction simulations made from small component conglomerates. This will be demonstrated through the following indicators:

-   Create material specific complex multi-leveled “Fractures” that allow for any two decompositions resulting from an impact to produce different patterns. ✅

#### Learning Goal 3:

Maintain gameplay performance whilst dynamically simulating environmental destruction. This learning goal will be measured as follows:

-   30fps\* must be maintained throughout the level for this project to be viable. ➖ (Average fps > 40, 1% low fps ~= 20-30)
-   60fps\* must be maintained throughout the level for this project to be considered sufficiently performant without the need for further improvements. ❌
-   If 90fps\* is maintained throughout the level this project can be considered very performant. ❌

\* Measurements taken on my PC (CPU: AMD Ryzen 7 5800X, RAM 32GB DDR4, GPU GeForce RTX 3070)

#### Learning Goal 4:

Incorporate real world physics calculations to improve simulation fidelity of environmental destruction. This will be demonstrated through:

-   The use of formulas such as the Krupp penetration formula to accurately calculate interactions between projectiles and models.➖
-   And/or utilize knowledge of these formulas to manipulate key variables of projectiles and target models to achieve the desired simulation effect for any given projectile against any given object. ✅

#### Learning Goal 5:

Operationalizing A previously unknown game Engine (UE5)

-   Built an executable file of the final tech demonstration in a distributable package.✅

## Week 1 - Selecting a Project

Topic selected = physics

Project Idea:

-   Create a small tech demonstration that expores the utility and application of Unreal Engine 5's Chaos Destruction system. Explore how the Chaos destruction system can be leveraged to create distinct, high fidelity, performant destructable meshes that feel like the material they are simulating when destroyed.
-   Create a number of different projectiles that can be utilised to destroy these destructable meshes in various ways to explore in depth the effects of differnt impact types and severitys on the accuracy and fidelity of the destructable meshes.

## Week 2 - Narrowing Focus & Tool Familiarisation

Narrowing Focus: It was decided I would not utilise complex aesthetic materials(textures) using simple colours to differentiate the different type of "physical" material. Additionally it was decided that I would only create a number of different walls instead of complete destructable structres in order to maintain the focus on creating the destructable fractures and not spend any additional time on creating or modeling more complex meshes.

Tool Familiarisation: I have already previously attempted a simillar feat within Unreal Engine 5 some years ago with litle success. However this previous attempt provided me with a simple UI, Game mode (used to manage game state and for global functions), first person character and movement, and a range of simple example fractures. This allowed me to rapidly re-familiarize myself with the functionality of Unreal Engine Blueprints as well as immediatley being work on these new fractures.
I therefore imported much of that previous project into this project to reduce extraneous workload that was out of scope of the objective.

 <div>
    <h3>Castle Smasher Existing Project</div>
       <img src="Images/CastleSmasherImage.jpg" alt="Castle Smasher Existing Project" width="500"/>
 </div>
(Milton, A. (2023). CastleSmasherGame. GitHub. https://github.com/XelaRonnoc/CastleSmasherGame)

Voxels: After some research into voxels and the resultant destructable effects that can be created using them, it was decided I would instead utilise Unreal Eninge 5's Chaos destruction system. This is because whilst voxels can allow for very powerful destructable environments it lacked a layer of realism and authenticity that Chaos destruction and Voronoi type fractures could provide.

## Week 3 - Research (Reading & Prototyping)

I conducted further research into environmental destruction within the video games industry and was able to observe three distic general methodologies/types of environmental desturction.

1. Lego brick destruction: where everything is made of components that can be seperated. This destruction has very high fidelity physics simulation but has a tendency to make everything look like legos being smashed apart. i.e. there are lots of small but complete pieces, not fragments or torn pieces.
 <div>
    <h3>Teardown example</div>
       <img src="https://www.gamereactor.eu/media/68/_3246893.png" alt="Teardown example" width="500"/>
 </div>

2. Scripted/baked destruction: where if a certain event happens or a threshold of damage is reached the game plays a scripted destuction effect/animation that is always the same and always ends in the same or very small number of different results. This destruction looks good aesthetically but quickly becomes obvious as to how it is working.
 <div>
    <h3>Battlefield example</div>
       <img src="https://cdn3.whatculture.com/images/2018/03/4990384945acf992-600x338.jpg" alt="Battlefield example" width="500"/>
 </div>

3. Non-actualised destruction. This isn't really destruction but is instead very high detailed physics simulations that do not have the actual visualised destruction but instead are able to make acurrate calculations of the physics and give life like results. The key place this occurs is games like war thunder where there is no true destruction but highly accurate physics, armour and projectile inteacitons take place to provide life like results in terms of a tanks or aircraft being destroyed or disabled.
 <div>
    <h3>Sniper Elite example</div>
       <img src="https://images.gamewatcherstatic.com/image/file/9/0d/13939/0037156.jpg" alt="Sniper Elite example" width="500"/>
 </div>

Relevance to this project:
Chaos destruction in UE5 is essentially just the lego brick approach. However the key difference is where the lego brick approach is a structure made of lots of pre-made blocks. Chaos starts as a structure that is then broken down into lots of blocks. This allows those blocks to consist of multiple levels of detail and provides far more interesting and unexpected breaks (not just along often visable seems). Even though under it all it functions in much the same way but in reverse.

## Week 4 - Research (Reading & Prototyping)

#### Prototyping:

Utilised a Chaos fracture based projectile to improve quality of interactions between mesh and projectile after watching a number of tutorials on Chaos destruction (Arputikos11 (2021) UE Chaos Destruction Tutorials. YouTube. https://www.youtube.com/playlist?list=PLheJxo1r1iYqahzl0-LWXfGiPxwvGvGtF). The utilisation of a chaos based projectile allows for the projectile and the destructable component to interact nativley without any need for futher tweaking or generation of the physics interaction manually. Additionally utilising a Chaos based projectile allows for projectile fragmentation futhering the potential for realistic destruction.

#### Issues:

One key issue is that small high velovity projectiles frequently clip whole or partly through the destructible component. This either prevents the collision interaction or causes a number of very strange and buggy collision interactions. I beleive this is caused by the colisions being checked only per each frame and as such then the projectile may have traveled past the wall between two frames and therefore two checks. I beleive this is also exacerbated further when the frame rate drops making me more convinced this is the issue.

Reasearch:
I additionally have looked into how to create the .exe for the final build of the project and found the following UE5 documentation which I will utilise to complete this (Epic Games. (n.d.). Preparing Unreal Engine projects for release. Unreal Engine Documentation. https://dev.epicgames.com/documentation/en-us/unreal-engine/preparing-unreal-engine-projects-for-release)

#### Other:

Defined learning goals and metrics.

## Week 5 - Presentations (& research/rescoping)

Completed project proposal. The base research component of this project has largley been complete however some further areas that require more investigation:

-   Creating custom fractures
-   How to calculate spalling
-   Deactivate or despawing of broken pieces after elapsed time
-   Improvement in small high velocity projectile collision detection

Completed project proposal presentation.

## Week 6 - Presentations (& research/rescoping)

#### Non-Technical Actions:

-   Begun work on research report, specifically layout, introduction section, and learnining goals section.
-   Created a timeline for the main project deliverables to ensure these are reached.

#### Technical Actions:

-   Created first iteration of concrete walls (Thick, medium, thin).
-   Tested concrete walls against "Rock" projectile.
-   Created physical foundations for wall sections as non-physical anchor fields caused incorrect and unrealistic fracture patterns.
    -   considered adding physical side and top supports also but eventually decided against it in favor of treating the walls as stand alone walls not as part of a larger structure.

## Week 7 - Research Report Finalisation

#### Non-Technical Actions:

-   Completed research report

#### Technical Actions:

-   Completed brick fracture 1st iteration (Thick, Medium, Thin).
    -   The in-built brick fracture patterns provided with Unreal Engine 5 had a number of issues that made them appear very unrealistic and therefore I created custom grid fractures to resemble true brick wall layouts.
-   Completed initial wood fracture iteration
    -   This wood fracture is currently very expensive on performance due to each fracture requiring around 3000 parts.
    -   Additionally because this fracture has such a number of small thin pieces there are a number of unexpected and very immersion breaking interactions that occur. As such this method of creating a wood fracture will likley have to be revisited later.
-   Attempted to improve performance by checking "Remove on Sleep" on the fracture patterns however in UE 5.2 there appears to be a bug with this feature that causes any fracture with this checked to disintegrate upon the first substantial hit ruining the simulation.

#### Next steps and Concerns:

-   It appears that performance will actually be one of the main issues with this project despite initally that not being a major concern of mine. Between the expensive wood fracture and the buggy removal function, the performance tanks to nearly 10fps when all walls are destroyed.
    -   I will continue looking into how to create better more performant wood fractures
    -   I will continue looking into the "Remove on Sleep" bug
-   Give all materials a final pass to improve fidelity and performance
-   Write the user testing questionaire.

## Week 8 - Project Development

#### Technical Actions:

-   Made minor improvements to Brick destruction fidelity

## Mid-semster break 1 - Continued R&D

#### Non-technical actions:

-   Created the inital draft of the User testing Questionaire.

#### Technical actions:

-   Added impact explosive projectile and tunned the effect
-   Added high velocity projectile

## Mid-semster break 1 - Continued R&D

#### Technical actions:

-   Tunned high velocity projectile
    -   Expereimented with utilsing CCD, and increasing the number of vertecies in the destructible meshes to only slight reliabilty improvment at the cost of performance.

#### Comments:

-   likley that I will have to remove the high velo projectile and attempt another projectile type

## Week 9 - Project Development

#### Technical actions:

-   Faster projetiles unticked update navigation in tick (under collision advanced) improving reliability slightly
-   For all chaos objects updated "Always create physics state" to true (under collision advanced) improving performance slightly
-   Updated explosive projectile to be a chaos based, improving collision detection and interactions.
-   Removed high velo projectile replaced with powerful timed explosive projectile with fragmentation
-   Upgraded to unreal engine 5.4 providing further features and optimisation for chaos destruction increasing performance significantly and reducing the number of physics bugs with both standard and high velocity projectiles
-   Added custom physics materials for each wall type to further improve simulation and interaction fidelity between meshes and further differentiate material properties.

## Week 10 - Project Development

#### Technical Actions:

-   Created a performant and high fidleity wood fracture utilising a combination of the original technique (to a lesser extent than before) and a significant use of noise within horizontal fractures to create a splintered looking effect to the breaks. This significantly increased initial render/creation time for the fracture (20-45mins per fracture) but reduced run-time performance impact significantly allowing for a maintainance of around 24fps in editor.
-   Utilised a simillar application of noise fractures to improve concrete and brick fractures.

<div>
<h3>Wood</div>
    <img src="Images/WoodFracture.png" alt="Wood Fracture" width="500"/>
</div>

<div>
    <h3>Brick</h3>
    <img src="Images/BrickFracture.png" alt="Brick Fracture" width="500"/>
</div>
<div>
    <h3>Concrete</h3>
    <img src="Images/ConcreteFracture.png" alt="Concrete Fracture" width="500"/>
</div>

## Week 11 - Project Evaluation

#### Technical Actions:

-   Built an executable version of the project (this requried complete rebuilds of all fractures made in UE 5.2)
-   Removed graphical bug related to Anti-Aliasing project settings

#### Non-technical Actions:

-   Improved Questionaire based feedback received from unit Convenor
    -   added discalmer section to play testing questionaire.
    -   improved multi choice question wording and format.
-   Begun work on collating data and creating final report including:
    -   Added learning goals, milestone, deliverables, and industry relevance sections to final report

## Week 12 - Project Evaluation

#### Technical actions:

-   Performed performance testing utilsing NVIDA FrameView
    -   30sec benchmark test duration.
        -   Test 1: AVG FPS 68.96, 1% Low FPS 22.83, Min FPS 19.99, Max FPS 155.71,
        -   Test 2: AVG FPS 48.76, 1% Low FPS 27.32, Min FPS 25.68, Max FPS 153.95,
        -   Test 3: AVG FPS 52.75, 1% Low FPS 28.92, Min FPS 23.96, Max FPS 154.92,
        -   Test 4: AVG FPS 54.83, 1% Low FPS 30.49, Min FPS 28.25, Max FPS 154.09,
        -   Test 5: AVG FPS 51.01, 1% Low FPS 26.62, Min FPS 25.12, Max FPS 158.56,
        -   Test 6: AVG FPS 53.70, 1% Low FPS 25.06, Min FPS 20.92, Max FPS 177.00,
        -   Test 7: AVG FPS 47.55, 1% Low FPS 21.95, Min FPS 21.19, Max FPS 154.84,
        -   Test 8: AVG FPS 44.01, 1% Low FPS 26.32, Min FPS 24.59, Max FPS 153.87,
        -   Test 9: AVG FPS 47.03, 1% Low FPS 24.38, Min FPS 19.90, Max FPS 149.21,
        -   Test 10: AVG FPS 53.03, 1% Low FPS 26.58, Min FPS 19.97, Max FPS 170.09,

<div>
    <h3>Performance Test Graph</h3>
    <img src="Images/PerfomanceTestGraph.png" alt="Performance Test Graph" width="800"/>
</div>

#### Non-technical actions

-   Sent built executable package to a number of play testers along with play testing questionaire.
-   Conducted in person playtesting with another group of play testers
-   Refine dev diary format

## Week 13 - Project Report & Deliverables Finalisation

#### Non-Technical Actions:

-   Completed user testing, unfortunatley was only able to conduct 8 tests within the available time
-   Compiled test responses, graphed quantitative responses
-   Complied qualitative responses and discuss implications of the comments here
-   Completed test reports and extended evaluation
-   Compiled documentation regarding constructions of destructable meshes and projectiles
-   Completed Portfolio video
-   Completed Final Report

<div>
    <h3>User Response Graph (Material Rating)</h3>
    <img src="Images/UserResponseMaterialGraph.png" alt="User Response Graph (Material Rating)" width="800"/>
</div>

<div>
    <h3>User Response Graph (Projectile Rating)</h3>
    <img src="Images/UserResponseProjectileGraph.png" alt="User Response Graph (Projectile Rating)" width="1000"/>
</div>

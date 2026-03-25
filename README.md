<p align="center">
  <img src="https://cdn.prod.website-files.com/69082c5061a39922df8ed3b6/69c3592d6746a06e2738ec69_DotGears.svg.png" alt="DOTGEARS" width="200" />
</p>

<h1 align="center">DOTGEARS</h1>

<p align="center">
  <strong>From the creator of Flappy Bird. Now building the future of AI-powered game creation.</strong>
</p>

<p align="center">
  <a href="https://twitter.com/dongatory"><img src="https://img.shields.io/badge/%40dongatory-verified-1DA1F2?style=flat-square&logo=x&logoColor=white" alt="@dongatory verified" /></a>
  <a href="https://vn.linkedin.com/in/dong-nguyen-095714138"><img src="https://img.shields.io/badge/Dong%20Nguyen-LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://bags.fm/AfvuTpZXLEkQ6CFG1kdw9Wx7wfCdTnVHhniUbxtDBAGS"><img src="https://img.shields.io/badge/bags.fm-%24dongatory-000000?style=flat-square" alt="bags.fm" /></a>
  <img src="https://img.shields.io/badge/Based_in-Hanoi%2C_Vietnam-DA251D?style=flat-square" alt="Hanoi, Vietnam" />
  <img src="https://img.shields.io/badge/Rust-stable-DEA584?style=flat-square&logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/License-Proprietary-red?style=flat-square" alt="License" />
</p>

<p align="center">
  <code>Contract Address: AfvuTpZXLEkQ6CFG1kdw9Wx7wfCdTnVHhniUbxtDBAGS</code>
</p>

---

## The Story

<table>
<tr>
<td width="140" align="center">
<img src="https://cdn.prod.website-files.com/69082c5061a39922df8ed3b6/69c3592e644b4e9a10cb3d45_21ZzpgClpiL.png" alt="Flappy Bird" width="100" />
</td>
<td>

In 2013 I built a game in three days. I called it Flappy Bird. Within months it was the most downloaded app on Earth -- 50 million downloads, $50,000 a day in ad revenue, number one in every app store on the planet.

Then I took it down.

I removed Flappy Bird at peak virality because I felt guilty about how addictive it had become. No acquisition. No pivot. No Series A. I walked away from one of the most successful mobile games ever made because it didn't sit right with me.

I don't regret that decision.

</td>
</tr>
</table>

<p align="center">
  <img src="https://cdn.prod.website-files.com/69082c5061a39922df8ed3b6/69c3592ec078ee1ce7498f08_flappy_bird_resize_article_hero_1.gif" alt="Flappy Bird Gameplay" width="280" />
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://cdn.prod.website-files.com/69082c5061a39922df8ed3b6/69c3592e9437c35f066dfdd9_bird_gif.gif" alt="Flappy Bird Animation" width="140" />
</p>

---

## DOTGEARS Studio

DOTGEARS is my software development company, headquartered in Hanoi. We have shipped multiple titles since Flappy Bird -- every one following the same design philosophy: light-hearted, easy to understand, kid-friendly, extremely difficult, and incredibly fun.

The games were never about scale. They were about craft. Small team, tight feedback loops, and an obsessive attention to the feel of a single tap.

```
DOTGEARS
16th Floor, Daeha Business Center
360 Kim Ma Street, Giang Vo Ward, Hanoi, Vietnam

Representative:    Nguyen Ha Dong
Contact:           contact@dotgears.com
Web:               dotgears.com
```

---

## What Comes Next

The same instinct that made Flappy Bird work -- that a game should be understandable in one second and playable forever -- now applies to how games are made.

I am building an AI-powered creation platform. The idea is radical in its simplicity: describe a game in plain language, and the system builds it. Not a prototype. Not a wireframe. A playable, shippable game with physics, rendering, audio, and input handling.

<p align="center">
  <img src="https://cdn.prod.website-files.com/69082c5061a39922df8ed3b6/69c35bb59c348d1205f808d3_67f53779742725a947b9a365_ai-game-vibe-coding-tool%20(1).png" alt="AI Game Creation Platform" width="720" />
</p>

The generation engine is written in Rust. Prompts compile into optimized bytecode that runs natively on iOS, Android, and web. No dependencies. No runtime. Just a binary that plays.

```rust
/// Prompt-to-game compilation pipeline
pub struct GameCompiler {
    parser: PromptParser,
    planner: MechanicPlanner,
    codegen: BytecodeEmitter,
    renderer: RenderGraph,
    physics: PhysicsConfig,
}

impl GameCompiler {
    /// Takes a natural language description and produces a shippable game binary.
    /// The pipeline is deterministic -- same prompt, same output, every time.
    pub fn compile(&self, prompt: &str) -> Result<GameBinary, CompileError> {
        let intent = self.parser.extract_intent(prompt)?;
        let mechanics = self.planner.resolve_mechanics(&intent)?;
        let bytecode = self.codegen.emit(&mechanics, &self.physics)?;
        let render_bindings = self.renderer.bind(&mechanics)?;

        Ok(GameBinary {
            bytecode,
            render_bindings,
            metadata: intent.metadata(),
        })
    }
}
```

The entity-component system handles everything a generated game needs. Collision detection, sprite animation, audio mixing, input routing, score tracking -- all resolved at compile time, not runtime.

```rust
/// Every game entity is a composition of components.
/// No inheritance. No virtual dispatch. Just data.
pub struct Entity {
    pub id: u64,
    pub position: Vec2,
    pub velocity: Vec2,
    pub sprite: SpriteHandle,
    pub collider: ColliderShape,
    pub behavior: BehaviorTree,
}

/// Fixed 60Hz physics step. Decoupled from render framerate.
/// Gravity, boundary clamping, and bounce are handled here.
pub fn physics_step(world: &mut World, dt: f32) {
    for entity in world.entities.iter_mut() {
        entity.velocity += world.gravity * dt;
        entity.position += entity.velocity * dt;

        if entity.position.y <= 0.0 || entity.position.y >= WORLD_HEIGHT {
            entity.velocity.y *= -BOUNCE_DAMPING;
            entity.position.y = entity.position.y.clamp(0.0, WORLD_HEIGHT);
        }
    }

    // Broad-phase collision sweep
    world.collision_grid.rebuild(&world.entities);
    for (a, b) in world.collision_grid.candidate_pairs() {
        if intersects(&world.entities[a].collider, &world.entities[b].collider) {
            world.event_queue.push(CollisionEvent { a, b });
        }
    }
}
```

---

## $GEARS

$GEARS exists to fund my entry into the [Bags.fm hackathon](https://bags.fm/AfvuTpZXLEkQ6CFG1kdw9Wx7wfCdTnVHhniUbxtDBAGS) -- bringing AI-powered game creation to the Bags ecosystem. A creator economy where anyone can build, publish, and monetize games from natural language.

I proved a three-day game can become the most downloaded app on Earth. Now I want to give everyone else the tools to do the same.

Trade $GEARS on [bags.fm/$dongatory](https://bags.fm/AfvuTpZXLEkQ6CFG1kdw9Wx7wfCdTnVHhniUbxtDBAGS).

---

| | |
|---|---|
| **Twitter** | [@dongatory](https://twitter.com/dongatory) |
| **Company** | [DOTGEARS](https://dotgears.com) |
| **LinkedIn** | [Nguyen Ha Dong](https://vn.linkedin.com/in/dong-nguyen-095714138) |
| **Bags** | [bags.fm/$dongatory](https://bags.fm/AfvuTpZXLEkQ6CFG1kdw9Wx7wfCdTnVHhniUbxtDBAGS) |
| **Email** | contact@dotgears.com |
| **Location** | Hanoi, Vietnam |

---

<p align="center">
  <sub>DOTGEARS -- Hanoi, Vietnam</sub><br/>
  <sub>Building the future of AI-powered game creation.</sub>
</p>

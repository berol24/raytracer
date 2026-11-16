# Discovery report

**Project:** Ray tracer for a film studio
**Date:** 16 November 2026

## Problem statement

A film studio needs a renderer it can own, extend and still explain after its authors leave, because its last in-house tool produced unexplained black spots, doubled its render time and slipped a delivery by three weeks, while the commercial licence that replaced it costs more than the studio can keep paying and blocks a new feature for months.

## Client interview summary

The client described a renderer the studio can own and still explain after its authors leave, and each point below cites the question and the answer it comes from. The Answer column is what the client said during the interview.

### Questions and answers

| ID | Question | Client's answer |
|---|---|---|
| Q1 | Walk me through the last time you rendered with your previous tool. | About 6 months ago, which is why this project exists. Black artefacts in the images, render time doubled, and nobody could say why. They bought a commercial licence and delivered 3 weeks late. |
| Q2 | What is a reasonable render time for you? | "I'm not too sure." The team needs images "really quickly". He hates seeing them start a render and then carry on. The middle of the sentence is unreadable. |
| Q3 | Which features do you need? | Requirements change on every project. "For the moment, let's say we need to be able to render spheres and planes. That's it for now." |
| Q4 | What is your deadline? | "The software must be delivered by January 5th", so the studio's team can start production. Repeated at the end: it must also produce a full film within 2 months. |
| Q5 | Are you using the reference solution on the market today? | Yes. It is very expensive, it does not cover future projects, the last project made a loss, and some features were sacrificed. |
| Q6 | What did you use before, and what do you use today? | An in-house tool that had bugs, then "a commercial solution, which was Maya." |
| Q7 | What kind of hardware do you have? | "Three levels." Designers have a powerful desktop and need a smaller preview. Production uses a larger machine. "We don't have graphics cards, so everything must be rendered by the CPU." |
| Q8 | Do you need an interface, or is a file enough? | Another tool writes "a standard file", the file goes on the render farm, a process is launched. "No interface at this point." |
| Q9 | What is the main thing you need? | "The ability to add our own features." With Maya, a specific feature is refused or takes "6 months or a year". |
| Q10 | How big is the farm? | "Up to 100 machines." RAM was mentioned and not captured. |
| Q11 | How long can final rendering take? | No more than 2 months once the creative work is done. |
| Q12 | How many creative renders do you do? | "At least 10 different pre-renders per image" before the final render. |
| Q13 | What will show you that the software meets your needs? | The same inputs always give the same output. An anomaly must be understood "within the same day". The black spots were "our biggest frustration". |
| Q14 | What is the target size? Is it 4K? How long is the film? | A 90-minute film. The frame rate in the dictation is "8 feet", which is not usable. Fast preview for the designer. High quality for the final scene. 4K was not confirmed. |
| Q15 | How will the scenes and images flow? | The designer places objects and lights in third-party software, saves a file, the renderer writes the image. Images are sequenced into a film, or looked at one by one. |
| Q16 | Do partner studios contribute? | They already render for the studio and have the skills to contribute. The studio keeps responsibility and wants their changes contributed "correctly". A few words were unreadable. |
| Q17 | Must all the code be open source? | "Currently, everything is open source." |
| Q18 | What kind of documentation do you need? | A development team will own the code, so technical people will read it. Also "some kind of user guide" for artists and for the people who set up scenes. |
| Q19 | Do you use a specific tool? | "Yes." The name was not captured. Maya is the only product the client named. |
| Q20 | What did you spend on rendering licences last year? | "Over $2 million." Seat-based: per machine, per artist, and every farm node. They want to bring it in-house. |
| Q21 | Is there anything we have missed? | What happens when the person who wrote the software leaves. After delivery, can the studio maintain it? If one team member leaves, can the others still understand the code? |
| Q22 | What happened to that team last time? | "A team of 5 people." The key person wrote the software, and "the other 5" could not debug it. |
| Q23 | What is your budget? | No more than €500,000. Last year's licence budget was $2 million, and the client called €500,000 one quarter of that. The money runs the development team they hire, and they expect the investment to be cheaper. |
| Q24 | Do you want an editing tool, or only rendering? | "We just want to render. It's a black box: it takes a description of the scene and produces images." |

### Findings by theme

Each point cites the row it comes from. **My conclusion** is mine, not the client's.

#### What went wrong

- Six months ago the in-house tool produced black spots, the render time doubled, and nobody could explain it. A commercial licence was bought and the delivery was 3 weeks late. *(Q1)*
- The author had left. The architectural choices were still in the code, and nobody could say why they had been made. *(Q21, Q22)*
- **My conclusion:** the studio needs two proofs. It can maintain the renderer after we leave, and any one developer can leave without taking the understanding with them.

#### What "good" means

- Same inputs, same image. *(Q13)*
- An anomaly explained, and a way to correct it, the same day. *(Q13)*

#### How the work is done

- No scene editor. A black box: a scene description in, images out. *(Q24)*
- No interface. A file from another tool is placed on the farm and a process is launched. *(Q8, Q15)*
- **My conclusion:** an interactive application is out of scope. The file format was not named.

#### Hardware and speed

- Designers: a powerful desktop, a smaller image, a fast preview. Production: a larger machine, high quality. No graphics cards. CPU only. *(Q7, Q14)*
- Farm: up to 100 machines. *(Q10)*
- Preview time: "really quickly", with no number of minutes. *(Q2)*
- Final rendering: at most 2 months after the creative work. At least 10 pre-renders per image. A 90-minute film. *(Q11, Q12, Q14)*
- **My conclusion:** ten pre-renders per image multiply the two-month budget. Without a frame rate and a resolution, that cannot become a minutes-per-frame target. CPU-only is a hard constraint.

#### What the first version must draw

- Spheres and planes for now. The tool must accept new requirements, because they change on every project. *(Q3)*
- The main need is to add the studio's own features. Maya refuses, or takes 6 to 12 months. *(Q9)*

#### Who owns the code

- Partner studios render for the client and should be able to contribute changes correctly. The studio keeps responsibility. *(Q16)*
- "Currently, everything is open source." *(Q17)*
- **My conclusion:** I read this as an open-source tool the studio still owns. "Currently" might instead describe the code they already have. That reading is open.

#### Money and deadline

- Ready on 5 January, and still able to render a full film in 2 months. *(Q4)*
- Last year: over 2 million dollars, a seat on every artist and every farm node, a loss, features sacrificed. They want the renderer in-house. *(Q5, Q6, Q20)*
- Cap of €500,000, which the client called one quarter of last year's $2 million, to run the development team they hire. *(Q23)*

#### Documentation

- Technical documentation for the developers who will own the code. A user guide for artists and for the people who set up scenes. *(Q18)*

### Open questions

- Frame rate and resolution. "8 feet" is not a frame rate, and 4K was not confirmed. *(Q14)*
- Preview time in seconds or minutes, and the unreadable clause in the first answer about render time. *(Q2)*
- RAM, CPU model, and whether the farm is the third hardware level. *(Q7, Q10)*
- The name behind "Yes" when a specific tool was asked. *(Q19)*
- Team size: a team of 5, then "the other 5". *(Q22)*
- The scene file format. *(Q8)*
- Whether "currently open source" is the tool they want or the code they have. *(Q17)*
- Which features were sacrificed, and which future needs Maya does not cover. *(Q5, Q9)*
- What "contribute their changes correctly" requires. *(Q16)*

## State of the art

Prices were checked on 16 November 2026. The same columns are used for every product. Commercial and open source are separated, because the client is leaving one and asking for the other.

### Commercial

| Solution | Maker | Licence | Pricing (16 November 2026) | Capabilities | Sources |
|---|---|---|---|---|---|
| Maya + Arnold | Autodesk | Commercial. Maya is a named-user seat. A farm needs one Arnold licence per node. | Maya 2,010 USD/year per seat, US price stated for 11 August 2026 in a guide still online on 16 November 2026. Arnold 430 USD/year per seat, reseller MSRP. Interactive Arnold inside Maya is included. Batch and farm rendering are not. | The tool the client moved to. Modelling, animation, lighting, film renderer. CPU and GPU. A new renderer feature waits on the vendor. | [Maya price guide](https://vagon.io/blog/how-much-does-maya-cost), [Arnold MSRP](https://cadmasters.com/autodesk/ARNOL), [Autodesk buy page](https://www.autodesk.com/products/arnold/buy) |
| RenderMan | Pixar | Commercial floating licence. The free licence is non-commercial, so it does not cover a film the studio sells. | 595 USD per licence, plus 250 USD per licence per year of maintenance. | Production path tracer used on Pixar films. One licence covers an artist seat or batch rendering. CPU and GPU. The studio does not own the source. | [RenderMan store](https://renderman.pixar.com/store/), [RenderMan 27 announcement](https://renderman.pixar.com/news/pixar-animation-studios-releases-renderman-27) |
| V-Ray Solo | Chaos | Commercial named-user subscription. | List price 540 USD/year (45 USD/month). The same page showed a 20% promotion at 432 USD/year. A farm contract is not published. It is a sales quote. | Production renderer plugged into Maya and other tools. CPU and GPU. The studio buys it and does not own the code. | [Chaos buy page](https://www.chaos.com/vray/buy-online) |

### Open source

| Solution | Maker | Licence | Pricing (16 November 2026) | Capabilities | Sources |
|---|---|---|---|---|---|
| Cycles | Blender project | Apache 2.0 for the library. Blender, the application, is GPL. | 0. No seat fee. | Production path tracer, CPU and GPU, used through Blender. The library can be built into another program. It is a full renderer, not a sphere-and-plane black box. | [Cycles](https://www.cycles-renderer.org/), [Blender licence](https://www.blender.org/about/license/), [GitHub](https://github.com/blender/cycles) |
| pbrt-v4 | Pharr, Jakob, Humphreys | Apache 2.0 | 0 for the code. The book is free online. The printed edition is sold. | A readable C++ ray tracer: scene file in, image out. Built to be studied, not to run a 100-machine farm. | [GitHub](https://github.com/mmp/pbrt-v4), [pbrt.org](https://pbrt.org), [the book](https://www.pbr-book.org/) |

Commercial tools can already render a film, and they are sold per seat or per node. That is the bill the client described: more than 2 million dollars, a licence on every artist and every farm machine, and a loss on the last project. A new feature stays with the vendor, which is the delay of 6 to 12 months the client hit with Maya. *(Q5, Q9, Q20)*

Open-source tools remove the seat fee and can be changed. Cycles is a real production renderer, and the application around it is a full tool under the GPL. The client asked for a black box in a pipeline that already has a scene tool. *(Q8, Q24)* pbrt-v4 is the closest readable C++ renderer with a scene file in and an image out, and it is a textbook implementation, not a farm product.

None of these, as shipped, is a CPU-only tool the studio owns, limited at first to spheres and planes, with the decisions written down so a colleague can explain a black pixel on the same day. *(Q3, Q7, Q13, Q21)*

## What is ray tracing?

A ray tracer takes a scene and produces an image. The scene describes shapes, lights and a camera. The image is a grid of pixels. For each pixel the tracer shoots a ray from the camera through that pixel into the scene, finds the closest shape the ray hits, and computes the colour from how light reaches that point. Light may come straight from a lamp or bounce off other shapes first. More bounces, and more rays per pixel, give a cleaner picture and take longer. That is why a small preview and a final film frame are not the same amount of work. *(Q7, Q14)*

**Sources:** I started from Scratchapixel, which walks through one ray per pixel, the hit, and the colour: https://www.scratchapixel.com/lessons/3d-basic-rendering/introduction-to-ray-tracing/raytracing-algorithm-in-a-nutshell.html. The reference I would come back to is *Physically Based Rendering*, free online, with the pbrt-v4 code beside it: https://www.pbr-book.org/.

## What is C++?

### Programming paradigms

C++ does not force one style.

| Paradigm | In C++ | Against JavaScript, which I use most |
|---|---|---|
| Procedural | Functions and structs, as in C | Functions, without a fixed layout in memory |
| Object-oriented | Classes, encapsulation, virtual functions | Objects and prototypes. The dispatch is hidden. |
| Generic | Templates, one piece of code for several types | No templates. Dynamic types do this job. |
| Functional | Lambdas and the algorithm headers | Functions are already values |

JavaScript hides the memory and lets me mix objects and functions freely. C++ lets me do the same mix, and it also lets me choose where each value lives and when it dies. It checks types at compile time, and it compiles to machine code. That is part of why it is used for renderers.

### What to watch out for

C++ leaves memory, object lifetime and a large set of errors to the programmer. JavaScript collects garbage and throws on many mistakes. C++ will compile a use of a freed object, an uninitialised variable, or a read past the end of an array, and the program then does whatever that memory happens to contain.

| Trap | What it does |
|---|---|
| Freed object, dangling reference | The code keeps using memory that no longer belongs to it |
| Uninitialised value, read past an array | The program reads whatever was already in that memory |
| Slicing | Copying a derived object into a base value drops the derived part |
| Undefined behaviour | A bug can vanish in a debug build and come back in release |
| Header and implementation | A change in a header rebuilds every file that includes it |

**My conclusion:** this class of bug matches the client's black spots that nobody could explain. *(Q1, Q13)* It is a hypothesis, not something the client said.

### Shaping the domain model

The client's domain, for this first version, is a scene of spheres and planes, a camera, lights, and an image. *(Q3, Q24)*

| Client concept | C++ shape | Why this shape |
|---|---|---|
| Sphere, plane | One type each, private data, a virtual "does this ray hit you?" | A new shape can be added without rewriting the tracer. *(Q3, Q9)* |
| Scene | A collection of shapes | Composition, not a deep hierarchy |
| Ray, colour, hit | Small values, passed by const reference | The render does not change the scene it was given. Same inputs, same image. *(Q13)* |
| Anything created with `new` | Visible ownership | There is no garbage collector |
| Every design choice | Written down | The last author left, and nobody could explain the code. *(Q21)* |

The core should not know which tool wrote the file. The client described a file in and an image out. *(Q8, Q24)*

**Sources:** I started from LearnCpp, which builds the language from types and functions up to classes and memory: https://www.learncpp.com/. The reference I would come back to is cppreference: https://en.cppreference.com/w/cpp. For the traps, the C++ Core Guidelines: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines.

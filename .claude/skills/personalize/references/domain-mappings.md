# Domain Mappings for Personalization

Every mathematical concept maps to a domain through a consistent pattern. Use the universal template below to create mappings for any domain, or reference the four worked examples.

---

## Core Concept Mappings (Universal Template)

| Math Concept | What to Map | Mapping Question to Ask |
|-------------|-------------|------------------------|
| **Vectors** | Measurements / state | "What's a list of numbers that describes something in my domain?" |
| **Vector addition** | Combining forces / effects | "What things combine additively in my domain?" |
| **Scalar multiplication** | Scaling / amplifying | "What scales up or down in my domain?" |
| **Dot product** | Alignment / similarity | "What two things do I compare for compatibility?" |
| **Projection** | Useful component | "When is only part of something useful?" |
| **Norms** | Magnitude / intensity | "What's the 'total size' of something?" |
| **Matrices** | Transformations / processes | "What process takes inputs and produces different outputs?" |
| **Matrix multiplication** | Sequential processes | "What processes happen in sequence?" |
| **Inverse** | Undoing a process | "What reverses something in my domain?" |
| **Singular matrix** | Information loss | "When is something irreversible?" |
| **Eigenvalues/vectors** | Natural axes / modes | "What are the fundamental independent factors?" |
| **SVD** | Hidden factor decomposition | "What hidden factors explain the patterns I see?" |
| **PCA** | Main sources of variation | "What's the #1 thing that differs between instances?" |

---

## Example Mappings by Interest

### Formula 1 Racing

| Math Concept | F1 Mapping |
|-------------|-----------|
| Vector | Car telemetry: `[speed, downforce, tire_temp, throttle]` |
| Vector addition | Forces on the car: engine + aero + cornering = net force |
| Scalar multiply | DRS boost (2x), braking (0.5x), spin (-1x) |
| Dot product | Setup alignment: "How well does this setup match the track?" |
| Projection | Corner exit speed projected onto the straight |
| Norms | Actual car speed (L2), total g-force sum (L1), peak g (L-inf) |
| Matrix | Setup change: transforms base performance into new profile |
| Composition | Multiple setup changes applied in sequence |
| Inverse | Reverting a setup change to baseline |
| Eigenvectors | Natural performance axes (straight-line speed vs cornering) |
| SVD | Driver-circuit recommender: predict performance at new tracks |

### Cooking & Recipes

| Math Concept | Cooking Mapping |
|-------------|----------------|
| Vector | Recipe: `[flour_g, sugar_g, butter_g, eggs, temp_C]` |
| Vector addition | Combining two recipes (mixing cookie dough + frosting) |
| Scalar multiply | Doubling a recipe (2x), halving (0.5x) |
| Dot product | Flavor compatibility: "How well do these ingredients go together?" |
| Projection | "How much of this spice blend is actually adding sweetness?" |
| Norms | Total calories (L1), richness score (L2), strongest flavor (L-inf) |
| Matrix | Cooking process: raw ingredients -> cooked dish transformation |
| Composition | Multi-step recipe: marinate -> sear -> braise |
| Inverse | "Unseasoning" -- what would neutralize this flavor? |
| Eigenvectors | Fundamental flavor axes: sweet-savory, rich-light, spicy-mild |
| SVD | Taste profile decomposition: predict if someone likes a new dish |

### Music & Audio

| Math Concept | Music Mapping |
|-------------|-------------|
| Vector | Audio frame: `[bass, mid, treble, tempo, loudness]` |
| Vector addition | Mixing two tracks together (layering) |
| Scalar multiply | Volume knob: amplify (2x), mute (0x), invert phase (-1x) |
| Dot product | Musical similarity: "How alike are these two songs?" |
| Projection | "How much bass is in this mix?" |
| Norms | Overall loudness (L2), total frequency energy (L1), peak frequency (L-inf) |
| Matrix | Equalizer: transforms flat audio into shaped output |
| Composition | Signal chain: EQ -> compression -> reverb |
| Inverse | Noise cancellation: undo the noise transformation |
| Eigenvectors | Natural resonant frequencies of an instrument |
| SVD | Listener-song recommender: predict if someone likes a new track |

### Basketball

| Math Concept | Basketball Mapping |
|-------------|-------------------|
| Vector | Player stats: `[points, assists, rebounds, steals, blocks]` |
| Vector addition | Team stats = sum of all player contributions |
| Scalar multiply | Minutes scaling: starter (1x) vs bench player (0.5x) |
| Dot product | Player-team fit: "How well does this player match what the team needs?" |
| Projection | "How much of this player's value is scoring vs playmaking?" |
| Norms | Overall impact (L2), box score total (L1), best single stat (L-inf) |
| Matrix | Coaching system: transforms raw talent into team performance |
| Composition | Play sequence: screen -> pass -> cut -> finish |
| Inverse | Defensive counter: undo the opponent's offensive play |
| Eigenvectors | Fundamental player archetypes (scorer, playmaker, defender) |
| SVD | Player-team matchup predictor from sparse scouting data |

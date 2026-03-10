# FNAAHS — Five Nights at Agoura High School
### Game Design Document v0.2

---

## Overview

| Field | Details |
|---|---|
| **Genre** | Survival Horror |
| **Platform** | Web Browser (HTML/JS, image-based) |
| **Perspective** | Static first-person — office desk POV |
| **Win Condition** | Survive each night from ~10:00 PM to 8:30 AM |
| **Lose Condition** | Caught by a teacher (see Kill Conditions) |

### Premise
You fell asleep in Mr. Oakman's office and got locked in the school overnight. Survive Monday through Friday. Each night gets harder. On Friday, nightmare versions of all teachers are active.

---

## Menu Screen

### Main Menu Layout
The main menu is displayed over a **still photograph of the school at night** — dark, empty hallways lit only by flickering fluorescent lights.

**Menu Options:**
- `NEW GAME` — Starts from Night 1 (Monday). Prompts confirmation if a save exists.
- `CONTINUE` — Resumes from the last completed night. Greyed out if no save exists.
- `NIGHTS` — Night select screen. Shows completed nights with a star. Locked nights show a padlock.
- `HOW TO PLAY` — Displays a brief tutorial screen (see below).
- `CREDITS` — Scrolling credits screen.

**Atmosphere:**
- Faint `night_ambience.mp3` plays on loop in the background.
- Occasionally, a distant `gentlemen.mp3` plays softly — just barely audible.
- No characters are visible on the menu screen. Presence is implied, not shown.
- Title text: large, bold, slightly distressed font. Subtitle beneath: *"Don't fall asleep in detention."*

### Night Select Screen
Displays five doors labeled **MON / TUE / WED / THU / FRI**.
- Completed nights show a faint light under the door.
- Current night pulses slightly.
- Locked nights are dark with a padlock icon.
- Clicking a completed night shows a brief summary of who was active and your best survive time.

### How To Play Screen
Displayed as a **sticky note on a desk**, handwritten-style font. Two pages, swipe or click to advance.

**Page 1 — The Basics:**
> You're stuck in Oakman's office until 8:30 AM.
> Watch the cameras. Manage your power.
> Close the door if someone gets close.
> The flashlight helps you check the room.
> If Mr. Keys locks on — call Jeff. Immediately.

**Page 2 — The Rules:**
> Don't stare at Oakmaster too long.
> Don't let Lepesto see you watching him.
> If Escobar gets in, answer her quiz. The Spanish is fake. Add O to everything.
> Killacky doesn't show up on cameras. She's just there. Or she isn't.
> Jeff saves you once. Once.

### Game Over Screen
- Background goes dark or white depending on who killed you (see character kill screens).
- Text: **GAME OVER** in large plain font.
- Subtext varies by killer (see character entries).
- Two buttons: `TRY AGAIN` and `MAIN MENU`.

### Win Screen (Per Night)
- School bell audio plays.
- Screen shows an empty hallway slowly brightening as morning light comes through windows.
- Text: **"The bell rings. You survived."**
- Night 5 (Friday) only: additional text — *"You made it through the week."*
- Button: `CONTINUE` (advances to next night or returns to menu on Friday).

---

## Characters

### Teachers (Antagonists)

---

#### Mrs. Killacky — *The Unseen*

**Mechanic:** Never appears moving on any camera. Simply materializes in Oakman's office without warning. No approach animation. She is just suddenly there.

**Kill:** Appears in the office — instant death. Screen goes dark. No jumpscare. Just gone.

**Counter:** None. Pure paranoia. Check the office view often.

**Unlocks:** Wednesday (Night 3)

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `killacky_roll.mp3` | Plays softly when Killacky is "in transit" — player cannot see her but she is moving |
| `killacky_voiceline1.mp3` | Plays when player has been looking at cameras too long without checking the office |
| `killacky_voiceline2.mp3` | Plays when Killacky was in the office but player was NOT looking — near miss |
| `killacky_voiceline3.mp3` | Plays randomly during her active window as ambient dread |
| `killacky_eat.mp3` | Game over sound — plays when Killacky kills the player |

*Suggested voice line content: unsettling ambient sounds, faint humming, or a single quiet word. No loud jumpscares — her horror is silence.*

**Game Over Screen — Killacky:**
- Screen cuts to black instantly. No image. No flash.
- Text: **GAME OVER**
- Subtext: *"You should have checked the room."*

---

#### Oakmaster (Mr. Oakman) — *The Wanderer*

**Mechanic:** Roams the school hallways. Visible on cameras. Says *"Gentlemen"* when spotted. If the player watches him on camera for too long, he locks eyes with the camera and charges toward the office at alarming speed. He is also alerted by lepesto.

**Kill:** Reaches the office door and breaks in.

**Counter:** Close the door before he arrives. Don't stare.

**Unlocks:** Monday (Night 1) — always first.

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `gentlemen.mp3` | Plays each time Oakmaster appears on a camera |
| `oakmaster_charge1.mp3` | Plays when he begins charging toward the office |
| `oakmaster_charge2.mp3` | Alternate charge line — plays if charge line already used recently |
| `oakmaster_door.mp3` | Plays when he reaches the office door |
| `oakmaster_gameover.mp3` | Game over sting when he kills the player |

*Suggested voice line content: "Gentlemen." delivered with increasing urgency each time. Charge line could be a loud echoing "GENTLEMEN!" down the hallway.*

**Game Over Screen — Oakmaster:**
- Flash of his close-up image, then black.
- Text: **GAME OVER**
- Subtext: *"You stared too long."*

---

#### Mr. McCreamy — *The Blinder*

**Mechanic:** Wanders hallways and "splurges" on cameras, covering the lens and temporarily disabling them. Does NOT kill directly. Forces the player blind on affected cameras, enabling other teachers to move untracked. The camera will show a static effect. Cleared on next night.

**Kill:** Does not kill. Enables other teachers by removing visibility.

**Counter:** Switch to unaffected cameras. Wait for cameras to clear.

**Unlocks:** Tuesday (Night 2)

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `cream.mp3` | Plays when McCreamy covers a camera — the sound of the camera being blocked |
| `static.mp3` | Plays on a blinded camera while it remains covered |
| `mccreamy_roam1.mp3` | Ambient sound when McCreamy is active and moving |
| `mccreamy_roam2.mp3` | Alternate ambient roam sound |
| `mccreamy_clear.mp3` | Plays when a blinded camera clears |

*Suggested voice line content: McCreamy does not speak. His sounds are environmental — wet, unsettling, abstract.*

---

#### Mrs. Escobar — *The Quiz Master*

**Mechanic:** Spanish teacher. Extremely strict. If she reaches the office, she does NOT kill immediately. Instead she forces a **Spanish Quiz Minigame**. Fail = death. Pass = she leaves... for now.

**Kill:** Fail the quiz within the time limit.

**Quiz Rules:**
- All answers are English words with `-o` added to the end.
- The quiz is **multiple choice** — one correct answer (`[word]o`) and one fake real Spanish word as a decoy.
- Example: *"Translate: run"* → correct answer is `runo`, decoy might be `correr`
- Example: *"Translate: jump"* → correct answer is `jumpo`, decoy might be `saltar`
- Time limit is tight. On Friday (Nightmare), time limit is shorter.
- Questions are randomly selected from a word bank.

**Counter:** Close the door before she reaches you.

**Unlocks:** Thursday (Night 4)

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `quiz_start.mp3` | Plays when Escobar reaches the office and quiz screen appears |
| `escobar_approach1.mp3` | Plays when Escobar is one camera node away from the office |
| `escobar_approach2.mp3` | Alternate approach line |
| `escobar_correct.mp3` | Short positive sting when player answers correctly |
| `escobar_wrong.mp3` | Game over sting when player answers wrong or times out |
| `escobar_leave.mp3` | Plays when Escobar leaves after a passed quiz |
| `escobar_roam1.mp3` | Ambient sound while Escobar is active and patrolling |

*Suggested voice line content: clipped, strict teacher tone. Approach lines like "I hope you studied." Game over line: a disappointed sigh.*

**Game Over Screen — Escobar:**
- Quiz screen lingers a moment, then red X overlay.
- Text: **GAME OVER**
- Subtext: *"Incorrect. See me after class."*

---

#### Mr. Keys — *The Stalker*

**Mechanic:** If Mr. Keys sees the player on camera, he **locks on permanently**. He walks slowly and steadily toward the office. Cannot be shaken. Closing the door does NOT stop him — he opens it. Cannot be distracted.

He repeats:
- *"You're my favorite student."*
- *"Stay after class."*

**Kill:** Reaches the player. Whispers *"Stay after class"* up close. Screen fades. GAME OVER.

**Counter:** **Jeff** (one-time use only — see Jeff entry).

**Unlocks:** Wednesday (Night 3)

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `youre_my_favorite.mp3` | Plays on loop while Keys is locked on and approaching |
| `stay_after_class.mp3` | Plays when Keys is close to the office / at the door |
| `keys_lockon.mp3` | Short sting that plays the moment Keys locks on to the player |
| `keys_door.mp3` | Sound of Keys opening the door |
| `keys_gameover.mp3` | Whispered game over line — *"Stay after class..."* |
| `keys_roam1.mp3` | Ambient sound while Keys is active but not yet locked on |
| `keys_roam2.mp3` | Alternate roam sound |

*Suggested voice line content: calm, unsettlingly cheerful tone throughout. The horror is in the pleasantness.*

**Game Over Screen — Mr. Keys:**
- Screen dims slowly. Keys appears in close-up.
- Audio: `keys_gameover.mp3` — whispered *"Stay after class..."*
- Text: **GAME OVER**
- Subtext: *"You should have called Jeff."*

---

### Staff (Protagonist)

---

#### Lepesto — *The Alerter*

**Mechanic:** Wanders the school as a staff member. Generally harmless. However, if the player lingers on his camera and he makes **direct eye contact** with the camera lens, he alerts all currently active teachers, causing a temporary speed surge.

**Kill:** Does not kill directly. Triggers teacher surge.

**Counter:** Look away from his camera before he makes eye contact (~3 second threshold, shorter on Friday).

**Unlocks:** Tuesday (Night 2)

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `lepesto_roam1.mp3` | Ambient sound as Lepesto wanders |
| `lepesto_roam2.mp3` | Alternate ambient roam |
| `lepesto_alert.mp3` | Plays the moment Lepesto makes eye contact and triggers the surge |
| `lepesto_suspicious.mp3` | Plays ~1 second before eye contact threshold — brief warning |

*Suggested voice line content: Lepesto doesn't know he's being watched. Alert line could be him calling out to a teacher by name down the hallway.*

---

#### Jeff (Golf Cart Jeff) — *The Hero*

**Mechanic:** Jeff patrols the school grounds on his golf cart. **One-time use per night.** When activated, Jeff arrives, the player hops in, and is relocated to a different room (classroom).

**Effect:** Permanently cancels Mr. Keys' lock-on for the rest of that night. The ONLY counter to Mr. Keys.

**Trade-off:** The new room has the same cameras but **two doors** instead of one — double the power drain.

**Unlocks:** Available every night from the start.

**Voice Lines & Audio:**
| File | Trigger |
|---|---|
| `jeff_cart.mp3` | Plays when Jeff is called and arriving |
| `jeff_save1.mp3` | Jeff line when he picks up the player — *"Hop in, kid."* or similar |
| `jeff_save2.mp3` | Alternate save line |
| `jeff_patrol.mp3` | Subtle ambient sound when Jeff is visible on Cam 7 (parking lot) |
| `jeff_used.mp3` | Short sad trombone or ambient sting when Jeff button is unavailable |

*Suggested voice line content: Jeff is friendly, casual, unbothered. He's seen things. He doesn't ask questions.*

**Jeff Save Sequence:**
- Player clicks Jeff button.
- `jeff_cart.mp3` plays — golf cart sound approaching.
- Brief transition screen: Jeff's image with a save line.
- Room swaps to classroom. Second door becomes active.
- Jeff button greys out for the rest of the night.

---

## Player Tools

### Security Cameras
- Monitor teacher locations across the school.
- Cycling through cameras costs no power.
- Watching Oakmaster too long triggers his charge.
- Watching Lepesto too long triggers his alert.
- McCreamy can white out individual cameras temporarily.
- Killacky **never** appears on cameras.

### Door
- Starting room (Oakman's office): **1 door**
- After Jeff relocates you: **2 doors**
- Each closed door drains power per tick.
- Doors stop most teachers from entering.
- Does **NOT** stop Mr. Keys — he opens it regardless.
- Power drains faster each night.

### Flashlight
- Used to check the office/room for Killacky.
- Reveals if a teacher is right outside the door.
- Battery is limited. Use sparingly.

### Jeff Button
- One-time use per night.
- Calls Jeff's golf cart for emergency extraction.
- Removes Mr. Keys' lock-on.
- Moves player to classroom with 2 doors.

---

## Night Progression (Monday – Friday)

### Night 1 — Monday
- **Active:** Oakmaster
- **Power drain:** Slow
- **Notes:** Tutorial night. Learn camera management and door timing. Oakmaster patrols slowly.

### Night 2 — Tuesday
- **Active:** Oakmaster, McCreamy, Lepesto
- **Power drain:** Moderate
- **Notes:** McCreamy begins blinding cameras. Lepesto introduced. Player must manage camera attention carefully.

### Night 3 — Wednesday
- **Active:** Oakmaster, McCreamy, Lepesto, Killacky, Mr. Keys
- **Power drain:** Moderate-High
- **Notes:** First night where both surprise death (Killacky) and inescapable death (Keys) are possible. Jeff becomes a critical resource.

### Night 4 — Thursday
- **Active:** All of the above + Mrs. Escobar
- **Power drain:** High
- **Notes:** Escobar adds quiz minigame pressure. Full roster active. Survival requires managing 6 threats simultaneously.

### Night 5 — Friday (Nightmare)
- **Active:** All teachers in NIGHTMARE MODE
- **Power drain:** Very High (~2x faster)
- **Changes:**
  - Oakmaster charges faster, says *"Gentlemen"* more frequently.
  - McCreamy blinds cameras in rapid succession.
  - Killacky can appear even without the player checking the office.
  - Escobar's quiz time limit is significantly shorter.
  - Keys moves noticeably faster after lock-on.
  - Lepesto's eye contact threshold is shorter.
- **Notes:** Survive until 8:30 AM. The school bell is salvation.

---

## Rooms & Camera Layout

### Starting Room: Oakman's Office
- **Doors:** 1 (north hallway)
- **Cameras:** Access to all school cameras
- **Desk:** Player POV. Flashlight on desk.

### Fallback Room: Classroom (via Jeff)
- **Doors:** 2 (front door + back door)
- **Cameras:** Same access as office
- **Risk:** Double door power drain. Use when Keys locks on.

### Camera Locations
| Cam | Location |
|---|---|
| CAM 1 | Main hallway — north (outside office door) |
| CAM 2 | Main hallway — south |
| CAM 3 | East corridor |
| CAM 4 | West corridor |
| CAM 5 | Cafeteria |
| CAM 6 | Stairwell |
| CAM 7 | Parking lot / exterior (Jeff's patrol zone) |
| CAM 8 | Classroom hallway (relevant after Jeff move) |

---

## Game Over Conditions

| Character | Kill Condition |
|---|---|
| **Killacky** | Appears in the office — instant, no warning |
| **Oakmaster** | Reaches door after being stared at on camera |
| **McCreamy** | Does not kill directly |
| **Escobar** | Player fails or times out on Spanish quiz |
| **Mr. Keys** | Reaches player after lock-on (no Jeff used) |
| **Lepesto** | Does not kill directly (triggers teacher surge) |

---

## File Structure

```
/FNAAHS/
  index.html              ← Entry point, loads game
  game.js                 ← Core game logic
  ui.js                   ← UI updates, camera switching
  teachers.js             ← Teacher AI / state machines
  audio.js                ← Sound management
  style.css               ← Layout and overlays

/FNAAHS/characters/
  oakmaster.png               ← Oakmaster on camera (static)
  oakmaster_charge.png        ← Oakmaster charging (close-up)
  mccreamy.png                ← McCreamy on camera
  mccreamy_splurge.png        ← McCreamy covering camera
  escobar.png                 ← Escobar on camera
  escobar_quiz.png            ← Escobar quiz screen close-up
  keys.png                    ← Keys on camera
  keys_close.png              ← Keys approaching (hallway)
  keys_gameover.png           ← Keys game over close-up
  lepesto.png                 ← Lepesto on camera
  jeff.png                    ← Jeff on golf cart (Cam 7)
  jeff_save.png               ← Jeff save transition screen
  killacky_gameover.png       ← Killacky in office (game over only)

/FNAAHS/backgrounds/
  office.png                  ← Player default room (Oakman's)
  classroom.png               ← Fallback room after Jeff move
  menu_bg.png                 ← Main menu background (school at night)
  cam1_hallway_n.png
  cam2_hallway_s.png
  cam3_east.png
  cam4_west.png
  cam5_cafeteria.png
  cam6_stairwell.png
  cam7_parking.png
  cam8_classroom_hall.png

/FNAAHS/ui/
  camera_panel.png            ← Camera switcher overlay
  door_button.png             ← Door close button
  jeff_button.png             ← Jeff call button
  jeff_button_used.png        ← Jeff button greyed out state
  power_bar.png               ← Power indicator
  flashlight_overlay.png      ← Flashlight circle effect
  howtoplay_page1.png         ← How to play sticky note page 1
  howtoplay_page2.png         ← How to play sticky note page 2

/FNAAHS/audio/

  — OAKMASTER —
  gentlemen.mp3               ← Oakmaster spotted on camera
  oakmaster_charge1.mp3       ← Oakmaster begins charging
  oakmaster_charge2.mp3       ← Alternate charge line
  oakmaster_door.mp3          ← Oakmaster reaches the door
  oakmaster_gameover.mp3      ← Oakmaster kills player

  — McCREAMY —
  cream.mp3                   ← Camera being blocked by McCreamy
  static.mp3                  ← Camera static while blinded
  mccreamy_roam1.mp3          ← McCreamy active ambient
  mccreamy_roam2.mp3          ← Alternate roam sound
  mccreamy_clear.mp3          ← Camera clears

  — ESCOBAR —
  quiz_start.mp3              ← Quiz screen appears
  escobar_approach1.mp3       ← Escobar one node away
  escobar_approach2.mp3       ← Alternate approach line
  escobar_correct.mp3         ← Correct answer sting
  escobar_wrong.mp3           ← Wrong answer / game over
  escobar_leave.mp3           ← Escobar leaves after passed quiz
  escobar_roam1.mp3           ← Escobar active ambient

  — MR. KEYS —
  keys_lockon.mp3             ← Keys locks on to player
  youre_my_favorite.mp3       ← Keys approaching (looped)
  stay_after_class.mp3        ← Keys near the office / at door
  keys_door.mp3               ← Keys opens the door
  keys_gameover.mp3           ← Whispered game over line
  keys_roam1.mp3              ← Keys active ambient (not locked)
  keys_roam2.mp3              ← Alternate roam sound

  — KILLACKY —
  killacky_roll.mp3           ← Killacky in transit (not visible)
  killacky_voiceline1.mp3     ← Player ignoring office too long
  killacky_voiceline2.mp3     ← Near miss — she was there
  killacky_voiceline3.mp3     ← Random ambient dread
  killacky_eat.mp3            ← Killacky kills player

  — LEPESTO —
  lepesto_roam1.mp3           ← Lepesto ambient wander
  lepesto_roam2.mp3           ← Alternate roam
  lepesto_suspicious.mp3      ← ~1 second warning before eye contact
  lepesto_alert.mp3           ← Eye contact confirmed — surge triggered

  — JEFF —
  jeff_cart.mp3               ← Jeff arriving on golf cart
  jeff_save1.mp3              ← Jeff save line ("Hop in, kid.")
  jeff_save2.mp3              ← Alternate save line
  jeff_patrol.mp3             ← Jeff visible on Cam 7 ambient
  jeff_used.mp3               ← Jeff button unavailable sound

  — GLOBAL —
  school_bell.mp3             ← 8:30 AM win condition
  night_ambience.mp3          ← Background loop (all nights)
  power_low.mp3               ← Warning when power is low
  power_out.mp3               ← Power hits zero
```

---

## Coding Overview (HTML/JS)

### Core Loop
- Game runs on a `setInterval` tick (every 500ms).
- Each tick: move teachers, check proximity, check player actions, update power, update camera views.
- Time runs from 10:00 PM to 8:30 AM (compressed real-time).
  - Night 1: 1 in-game hour ≈ 45 real seconds
  - Night 5: 1 in-game hour ≈ 30 real seconds

### Teacher State Machine
Each teacher has its own state machine:
```
IDLE → MOVING → PROXIMATE → ATTACKING
```
- Each teacher has a `position` (camera node) and a `target`.
- Movement speed increases each night.
- Mr. Keys has an additional `LOCKED_ON` state that bypasses normal logic.

### Camera System
- `currentCamera` variable tracks which cam is displayed.
- Each camera background image swaps on selection.
- Teacher images composite on top of background if teacher is at that camera node.
- McCreamy: on splurge, overlay white PNG on that camera.
- Killacky: never placed on camera nodes. Checked via random interval tick against office view.

### Door System
- `doorClosed = true/false` (two booleans after Jeff move).
- While closed: drains power each tick.
- If teacher reaches door node AND door is open: they enter.
- Keys exception: he opens a closed door regardless.

### Power System
- `power = 100`, drains to 0.
- Drain rate increases per night.
- Each closed door adds to drain rate.
- At `power = 0`: all doors open, flashlight dies, `power_out.mp3` plays.

### Jeff Save
```javascript
jeffUsed = false  // reset each night

// On activation:
// 1. Play jeff_cart.mp3
// 2. Show jeff_save.png transition screen
// 3. Play jeff_save1.mp3 or jeff_save2.mp3
// 4. Set currentRoom = "classroom"
// 5. Enable second door
// 6. Cancel Keys LOCKED_ON state
// 7. Set jeffUsed = true — disable button
```

### Escobar Quiz Minigame
- Triggered when Escobar reaches the office (door open).
- Overlay quiz screen with `quiz_start.mp3`.
- Display: `"Translate: [english word]"`
- Two choices: `[word]o` (correct) vs. a real Spanish word (decoy).
- Timer bar counts down. Wrong answer or timeout = GAME OVER.
- Questions randomly selected from word bank (minimum 30 words recommended).

### Lepesto Eye Contact
```javascript
// If player views Lepesto's camera:
//   start eyeContactTimer
//   threshold = ~3000ms (Night 1-4), ~1500ms (Night 5)
//   play lepesto_suspicious.mp3 at ~1000ms as warning
//   on threshold: play lepesto_alert.mp3, trigger teacherSurge()
//   teacherSurge() increases all teacher speeds for 10 ticks
```

### Killacky
```javascript
// Every X seconds (random interval):
//   roll killacky appearance chance
//   if player IS viewing office or desk: GAME OVER
//   if player is NOT viewing office:
//     she was there but left — flicker office cam
//     play killacky_voiceline2.mp3
// Frequency and chance increase on Night 5
```

### Win Condition
- `gameTime` reaches 8:30 AM on any night.
- Play `school_bell.mp3`.
- Show win screen: *"The bell rings. You survived."*
- Night 5 only: *"You made it through the week."*
- Advance to next night or return to menu.

---

## Night Intro Dialogue (Phone Guy)

**Monday:**
> "Hey, youre not supposed to be here. Oakmaster isnt going to be very happy. Dont look too long, ill try and get you out on friday. Good luck."

**Tuesday:**
> "Mr. Mcreamy is coming. Watch out for lepesto, he might radio your location in. Im allmost there, hold off untill friday."

**Wednesday:**
> "So. Um. Mrs. Killacky. We don't really know how she moves. Or if she moves. She's just... sometimes there. Also Mr. Keys is active tonight. If he sees you, just call Jeff. Don't wait. Call Jeff immediately. Remeber, you only get jeff once."

**Thursday:**
> "Mrs. Escobar is patrolling tonight. If she gets in, she will quiz you. You'll figure it out. Probably. Keep the door closed."

**Friday:**
> (Static)

---

*FNAAHS GDD v0.2 — last updated Night 5*

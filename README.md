================================================================
FNAAHS — FIVE NIGHTS AT AGOURA HIGH SCHOOL
GAME DESIGN DOCUMENT v0.1
================================================================

OVERVIEW
--------
Genre:        Survival Horror (Comedy)
Platform:     Web Browser (HTML/JS, image-based)
Perspective:  Static first-person (office desk POV)
Win Condition: Survive each night from ~10:00 PM to 8:30 AM
               when school starts and someone finds you.
Lose Condition: Caught by a teacher (see kill conditions)

PREMISE
-------
You fell asleep in Mr. Oakman's office and got locked in the
school overnight. Survive Monday through Friday. Each night
gets harder. On Friday, nightmare versions of all teachers
are active.

================================================================
CHARACTERS
================================================================

--- TEACHERS (Antagonists) ---

MRS. KILLACKY
  Role:      The Unseen
  Mechanic:  Never appears moving on any camera. Simply
             materializes in Oakman's office without warning.
             No audio cue. No approach animation. She is just
             suddenly there.
  Kill:      Appears in the office — instant death.
             Screen goes dark. No jumpscare. Just gone.
  Counter:   None. Pure paranoia. Check the office view often.
  Unlocks:   Wednesday (Night 3)

OAKMASTER (Mr. Oakman)
  Role:      The Wanderer
  Mechanic:  Roams the school hallways. Appears on cameras
             saying "Gentlemen." If the player watches him
             on camera for too long, he locks eyes with the
             camera and charges toward the office at alarming
             speed.
  Kill:      Reaches the office door and breaks in.
  Counter:   Close the door before he arrives. Don't stare.
  Audio cue: "Gentlemen." (repeated, escalating pace)
  Unlocks:   Monday (Night 1) — he is always first.

MR. McCREAMY
  Role:      The Blinder
  Mechanic:  Wanders hallways and "splurges" on cameras,
             covering the lens in white and temporarily
             disabling them. Does NOT kill directly.
             Forces the player blind on affected cameras.
  Kill:      Does not kill. Enables other teachers by
             removing the player's ability to track them.
  Counter:   Switch to unaffected cameras. Wait for cameras
             to clear. Use flashlight as backup.
  Unlocks:   Tuesday (Night 2)

MRS. ESCOBAR
  Role:      The Quiz Master
  Mechanic:  Spanish teacher. Extremely strict. If she
             reaches the office, she does NOT kill immediately.
             Instead she forces a Spanish Quiz Minigame.
             Fail = death. Pass = she leaves... for now.
  Kill:      Fail the quiz within the time limit.
  Quiz Rules:
    - All answers are English words with "-o" added to the end.
    - Example: "What is the word for run?" → "runo"
    - Example: "Translate: jump" → "jumpo"
    - Questions appear fast. Time limit is tight.
    - On nightmare mode (Friday), the time limit is shorter.
  Counter:   Close the door before she reaches you.
  Unlocks:   Thursday (Night 4)

MR. KEYS
  Role:      The Stalker
  Mechanic:  If Mr. Keys sees the player on camera, he locks
             on. From that point he CANNOT be shaken. He walks
             slowly and steadily toward the office, repeating:
               - "You're my favorite student."
               - "Stay after class."
             Closing the door does NOT stop him. He will open it.
             He cannot be distracted by the phone decoy.
  Kill:      Reaches the player. Whispers "Stay after class"
             up close. Screen fades. GAME OVER.
  Counter:   JEFF (one-time use only, see below).
  Unlocks:   Wednesday (Night 3)

--- STAFF (Neutral / Protagonist) ---

LEPESTO
  Role:      The Alerter
  Mechanic:  Wanders the school as a staff member. Generally
             harmless. However, if the player lingers on his
             camera and he makes direct eye contact with the
             camera lens, he becomes suspicious and alerts all
             currently active teachers, causing them to speed
             up temporarily.
  Kill:      Does not kill directly. Triggers teacher surge.
  Counter:   Look away from his camera before eye contact.
  Unlocks:   Tuesday (Night 2)

JEFF (Golf Cart Jeff)
  Role:      The Hero
  Mechanic:  Jeff patrols the school grounds on his golf cart.
             One-time use emergency escape. When activated,
             Jeff arrives, the player hops in the golf cart,
             and is relocated to a DIFFERENT ROOM (classroom).
  Effect:    Cancels Mr. Keys' lock-on permanently for that
             night. The ONLY counter to Mr. Keys.
  Trade-off: The new room has the SAME cameras but TWO doors
             instead of one, meaning double the power drain
             to keep both doors closed.
  Use:       Single use per night. Choose wisely.
  Unlocks:   Available every night as a passive option.

================================================================
PLAYER TOOLS
================================================================

SECURITY CAMERAS
  - Monitor teacher locations across the school.
  - Cycling through cameras costs no power.
  - Watching Oakmaster too long triggers his charge.
  - Watching Lepesto too long triggers his alert.
  - McCreamy can white out individual cameras.
  - Killacky never appears on cameras (she teleports).

DOOR
  Starting room (Oakman's office): 1 door.
  After Jeff relocates you:        2 doors.
  - Each door costs power to hold closed.
  - Doors stop most teachers from entering.
  - Does NOT stop Mr. Keys.
  - Power drains faster each night.

FLASHLIGHT
  - Used to check the office/room for Killacky.
  - Reveals if a teacher is RIGHT outside the door.
  - Battery is limited. Use sparingly.

PHONE (Decoy)
  - Place the phone somewhere in the hallway via camera view.
  - When a teacher passes near it, they are drawn toward it.
  - Buys time to manage doors or check cameras.
  - Does NOT work on Mr. Keys.
  - Recharge time between uses.

JEFF BUTTON
  - One-time use per night.
  - Calls Jeff's golf cart for emergency extraction.
  - Removes Mr. Keys' lock-on.
  - Moves player to classroom with 2 doors.

================================================================
NIGHT PROGRESSION (Monday – Friday)
================================================================

NIGHT 1 — MONDAY
  Active: Oakmaster
  Power drain: Slow
  Notes: Tutorial night effectively. Learn camera management
         and door timing. Oakmaster patrols slowly.

NIGHT 2 — TUESDAY
  Active: Oakmaster, McCreamy, Lepesto
  Power drain: Moderate
  Notes: McCreamy begins blinding cameras. Lepesto introduced.
         Player must manage camera attention carefully.

NIGHT 3 — WEDNESDAY
  Active: Oakmaster, McCreamy, Lepesto, Killacky, Mr. Keys
  Power drain: Moderate-High
  Notes: First night where surprise death (Killacky) and
         inescapable death (Keys) are both possible.
         Jeff becomes critical resource.

NIGHT 4 — THURSDAY
  Active: All of the above + Mrs. Escobar
  Power drain: High
  Notes: Escobar adds quiz minigame pressure. Full roster.
         Survival requires managing 6 threats simultaneously.

NIGHT 5 — FRIDAY (NIGHTMARE)
  Active: All teachers in NIGHTMARE MODE
  Power drain: Very High (drains ~2x faster)
  Changes:
    - Oakmaster charges faster, says "GENTLEMEN" more often.
    - McCreamy blinds cameras in rapid succession.
    - Killacky can appear even without checking cameras.
    - Escobar's quiz time limit is significantly shorter.
    - Keys moves noticeably faster after lock-on.
    - Lepesto alerts on a shorter eye contact window.
  Notes: Survive until 8:30 AM. The school bell is salvation.

================================================================
ROOMS & CAMERA LAYOUT
================================================================

STARTING ROOM: OAKMAN'S OFFICE
  Doors: 1 (north hallway)
  Cameras visible from here: All school cameras
  Desk: Player POV. Flashlight on desk. Phone on desk.

FALLBACK ROOM: CLASSROOM (via Jeff)
  Doors: 2 (front door + back door)
  Cameras: Same camera access as office.
  Risk: Double door power drain. Choose when Keys locks on.

CAMERA LOCATIONS (suggested):
  CAM 1 — Main hallway (north, outside office door)
  CAM 2 — Main hallway (south)
  CAM 3 — East corridor
  CAM 4 — West corridor
  CAM 5 — Cafeteria
  CAM 6 — Stairwell
  CAM 7 — Parking lot / exterior (Jeff's patrol zone)
  CAM 8 — Classroom hallway (relevant after Jeff move)

================================================================
GAME OVER CONDITIONS
================================================================

  KILLACKY:   Appears in the office. Instant. No warning.
  OAKMASTER:  Reaches the door and enters after being stared at.
  McCREAMY:   Does not kill directly.
  ESCOBAR:    Player fails Spanish quiz within the time limit.
  MR. KEYS:   Reaches the player after lock-on (no Jeff used).
  LEPESTO:    Does not kill directly (triggers teacher surge).

GAME OVER SCREEN — MR. KEYS:
  Screen dims. Mr. Keys appears in close-up.
  Audio: (whispered) "Stay after class..."
  Text: GAME OVER
  Subtext: You should have called Jeff.

================================================================
FILE STRUCTURE (Web Game)
================================================================

If splitting into multiple files:
  /FNAAHS/
    index.html            ← Entry point, loads game
    game.js               ← Core game logic
    ui.js                 ← UI updates, camera switching
    teachers.js           ← Teacher AI/state machines
    audio.js              ← Sound management
    style.css             ← Layout and overlays

  /FNAAHS/characters/
    oakmaster.png         ← Oakmaster on camera (static)
    oakmaster_charge.png  ← Oakmaster charging (close-up)
    mccreamy.png          ← McCreamy on camera
    mccreamy_splurge.png  ← McCreamy covering camera
    escobar.png           ← Escobar on camera
    escobar_quiz.png      ← Escobar quiz screen close-up
    keys.png              ← Keys on camera
    keys_close.png        ← Keys approaching (hallway)
    keys_gameover.png     ← Keys game over close-up
    lepesto.png           ← Lepesto on camera
    jeff.png              ← Jeff on golf cart
    jeff_save.png         ← Jeff save sequence
    killacky_gameover.png ← Killacky appears (office view only)

  /FNAAHS/backgrounds/
    office.png            ← Player's default room (Oakman's)
    classroom.png         ← Fallback room after Jeff move
    cam1_hallway_n.png    ← Camera 1 background
    cam2_hallway_s.png
    cam3_east.png
    cam4_west.png
    cam5_cafeteria.png
    cam6_stairwell.png
    cam7_parking.png
    cam8_classroom_hall.png

  /FNAAHS/ui/
    camera_panel.png      ← Camera switcher overlay
    door_button.png       ← Door close button
    phone_button.png      ← Phone decoy button
    jeff_button.png       ← Jeff call button
    power_bar.png         ← Power indicator
    flashlight_overlay.png← Flashlight circle effect

  /FNAAHS/audio/
    gentlemen.mp3         ← Oakmaster line
    youre_my_favorite.mp3 ← Keys line
    stay_after_class.mp3  ← Keys line / game over whisper
    quiz_start.mp3        ← Escobar quiz sting
    jeff_cart.mp3         ← Golf cart sound
    school_bell.mp3       ← 8:30 AM win condition
    static.mp3            ← Camera static (McCreamy)
    night_ambience.mp3    ← Background loop

================================================================
CODING OVERVIEW (HTML/JS Web Game)
================================================================

CORE LOOP
  - Game runs on a setInterval tick (e.g. every 500ms).
  - Each tick: move teachers, check proximity, check player
    actions, update power, update camera views.
  - Time runs from 10:00 PM to 8:30 AM (compressed real-time).
    Suggested: 1 in-game hour = ~45 real seconds on Night 1,
    scaling down to ~30s by Night 5.

TEACHER STATE MACHINE (per teacher)
  States: IDLE → MOVING → PROXIMATE → ATTACKING
  - Each teacher has a position (camera node) and a target.
  - Movement speed increases each night.
  - Special states: KEYS has LOCKED_ON state (ignores phone).

CAMERA SYSTEM
  - currentCamera variable tracks which cam is displayed.
  - Each camera background image swaps on selection.
  - Teacher images composite on top of background if teacher
    is at that camera node.
  - McCreamy: on splurge, overlay white PNG on that camera.
  - Killacky: never placed on camera nodes. Checked separately
    via random interval tick against office view.

DOOR SYSTEM
  - doorClosed = true/false (two booleans after Jeff move).
  - While closed: drains power each tick.
  - If teacher reaches door node AND door is open: they enter.
  - Keys exception: he opens a closed door regardless.

POWER SYSTEM
  - power = 100, drains to 0.
  - Drain rate increases per night.
  - Each closed door adds to drain rate.
  - At power = 0: all doors open, flashlight dies.

PHONE DECOY
  - Player selects a camera hallway to place phone.
  - phoneLocation = camera node ID.
  - Any teacher (except Keys) within 1 node redirects to phone.
  - After X seconds, phone effect wears off.

JEFF SAVE
  - jeffUsed = false per night.
  - On activation: play cart audio, swap room background,
    set currentRoom = "classroom", enable second door,
    cancel Keys lockOn state.
  - jeffUsed = true. Button disabled for remainder of night.

ESCOBAR QUIZ MINIGAME
  - On Escobar reaching the door (if open):
    Overlay quiz screen.
    Display: "Translate: [english word]"
    Answer input field.
    Timer bar counts down.
    Correct answer = "[word]o"
    Wrong answer or timeout = GAME OVER.
    Questions are randomly selected from a word bank.

LEPESTO EYE CONTACT
  - If player views Lepesto's camera, start eyeContactTimer.
  - Timer threshold = ~3 seconds (shorter on Friday).
  - On threshold reached: trigger teacherSurge() for 10 ticks.

KILLACKY
  - Every X seconds (random interval), roll a chance that
    Killacky "appears" in the office.
  - If player is currently viewing office camera or desk view:
    Show killacky_gameover.png. GAME OVER.
  - If player is NOT viewing office: she was there but left.
    Show brief flicker on office cam to hint her presence.
  - Frequency increases on Friday.

WIN CONDITION
  - gameTime reaches 8:30 AM.
  - Play school_bell.mp3.
  - Show win screen: "The bell rings. You survived."
  - Unlock next night.

================================================================
PHONE GUY INTRO DIALOGUE (suggestions per night)
================================================================

MONDAY:
  /phone/monday.mp3
  Oakman
  "Gentelmen, what are you doing in my office after hours, get out of there!"

TUESDAY:
  /phone/tuesday.mp3
  "Gentelmen, it appears mr mccreamy isnt too happy"

WEDNESDAY:
  /phone/
  "So. Um. Mrs. Killacky. Yeah. We don't really know how she
  moves. Or if she moves. She's just... sometimes there.
  Also Mr. Keys is active tonight. If he sees you, just...
  call Jeff. Don't wait. Call Jeff immediately."

THURSDAY:
  /phone/
  "Mrs. Escobar is patrolling tonight. If she gets in,
  she will quiz you. The Spanish is... not real Spanish.
  You just add O to things. Run is runo. Jump is jumpo.
  You'll figure it out. Probably. Keep the door closed."

FRIDAY:
  /phone/
  "...I'm not going to sugarcoat it.
  Everyone is faster tonight. Killacky is worse.
  Keys is worse. The power drains like crazy.
  You have Jeff. Use him smart.
  Survive until 8:30.
  The bell will save you.
  Good luck."

================================================================
END OF DOCUMENT — FNAAHS GDD v0.1
================================================================

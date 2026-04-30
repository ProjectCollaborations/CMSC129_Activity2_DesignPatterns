# UPV Dating App with a Twist: Design Pattern Implementation

## Table of Contents

- [A. App Summary](#a-app-summary)
- [B. Design Pattern Implementation](#b-design-pattern-implementation)
  - [Pattern 1: Creational - Factory Pattern](#pattern-1-creational---factory-pattern)
    - [i. Name of Pattern](#i-name-of-pattern)
    - [ii. Concept](#ii-concept)
    - [iii. Visual Diagram](#iii-visual-diagram)
    - [iv. Why it Works Nga](#iv-why-it-works-nga)
    - [v. Pseudocode](#v-pseudocode)
  - [Pattern 2: Behavioral - Observer Pattern](#pattern-2-behavioral---observer-pattern)
    - [i. Name of Pattern](#i-name-of-pattern-1)
    - [ii. Concept](#ii-concept-1)
    - [iii. Visual Diagram](#iii-visual-diagram-1)
    - [iv. Why it Works](#iv-why-it-works-nga-1)
    - [v. Pseudocode](#v-pseudocode-1)
  - [Pattern 3: Structural - Adapter Pattern](#pattern-3-structural---adapter-pattern)
    - [i. Name of Pattern](#i-name-of-pattern-2)
    - [ii. Concept](#ii-concept-2)
    - [iii. Visual Diagram](#iii-visual-diagram-2)
    - [iv. Why it Works](#iv-why-it-works-nga-2)
    - [v. Pseudocode](#v-pseudocode-2)
- [C. Initial Pattern Summary](#c-initial-pattern-summary)
- [D. Final Notes](#d-final-notes)

---

# A. App Summary

## App Name

**IskoMatch**

## App Idea

**IskoMatch** is a UPV dating app designed for students who want to meet potential matches through personality, shared campus experiences, and student-life interests rather than just profile pictures.

The app lets users create a student dating profile containing basic information such as:

- Name or nickname
- Course and year level
- Interests
- Favorite UPV spots
- Study habits
- Personality preferences
- Type of connection they are looking for

The app then suggests possible matches based on compatibility, shared interests, and campus-related preferences.

---

## The Twist: Mystery Match Quest

The unique twist of **IskoMatch** is called **Mystery Match Quest**.

Instead of showing the full profile immediately, the app slowly reveals profile details through short campus-themed quests. This makes the matching experience more fun, less appearance-based, and more connected to UPV student life. 

For example, instead of immediately showing the user’s full name and photo, the app may first show a clue like:
```text
A CMSC student who likes beach sunsets, quiet study sessions, and spontaneous food trips after class.
```
## B. Design Pattern Implementation
## Pattern 1: Creational - Factory Pattern

### i. Name of Pattern
Creational – Factory Pattern

---

### ii. Concept

The Factory Pattern is a creational design pattern na ginagmait kung the app needs to create different types of related objects, pero we do not want the object creation logic to be kalat everywhere.

Parang may isang "factory" sa app na responsible for creating objects. Instead of every screen saying, "If this is an icebreaker, create this. If this is a campus quest, create that," the screen just asks the factory: "Please create the quest I need."

This is usually used when there are many possible object types, but they belong to the same family or category. In IskoMatch, it is applied to the **Mystery Match Quest** feature because the app needs to create different types of quests:

- IcebreakerQuest
- CampusSpotQuest
- PersonalityQuest
- StudyHabitQuest

Instead of creating these manually in different screens, the app uses a **QuestFactory**.

---

### iii. Visual Diagram

``` mermaid
flowchart TD
  subgraph WITHOUT["❌ WITHOUT Factory Pattern"]
    A1[MatchScreen] -->|if icebreaker| B1[new IcebreakerQuest]
    A1 -->|if campus_spot| C1[new CampusSpotQuest]
    A2[ProfileScreen] -->|if icebreaker| B2[new IcebreakerQuest]
    A2 -->|if personality| D2[new PersonalityQuest]
    A3[ChatScreen] -->|if study_habit| E3[new StudyHabitQuest]
    A3 -->|if campus_spot| C3[new CampusSpotQuest]
  end

  subgraph WITH["✅ WITH Factory Pattern"]
    S1[MatchScreen] --> F[QuestFactory]
    S2[ProfileScreen] --> F
    S3[ChatScreen] --> F
    F -->|icebreaker| Q1[IcebreakerQuest]
    F -->|campus_spot| Q2[CampusSpotQuest]
    F -->|personality| Q3[PersonalityQuest]
    F -->|study_habit| Q4[StudyHabitQuest]
end
```

---

### iv. Why it Works Nga

**Without Factory Pattern**

Without the Factory Pattern, bawat screen na kailangan gumawa ng quest may sariling logic. So for example, the Match Screen, Profile Screen, and Chat Screen might all have paulit-ulit na if-else statements just to decide which quest object ang gagawin.

Problematic siya because:
- Paulit-ulit yung creation logic.
- Mas mahirap i-maintain.
- If may bagong quest type, maraming files ang kailangan baguhin.
- May chance na inconsistent ang paggawa ng quest per screen.
- Nagiging messy yung code kasi the screens are doing too much.

For example, if the team adds a new `OrgLifeQuest`, kailangan i-update lahat ng screens na may quest creation logic.

| ❌ Without Factory Pattern | ✅ With Factory Pattern |
|---|---|
| Scattered creation logic across screens | Centralized creation in QuestFactory |
| Repeated if-else in every screen | Screens just call `QuestFactory.createQuest(type)` |
| Must update many files for new quest types | Only factory needs updating for new types |
| Risk of inconsistent quest creation | Consistent quest creation guaranteed |
| Screens are doing too much | Screens stay focused on their own logic |

**With Factory Pattern**

With the Factory Pattern, mas clean siya because may isang `QuestFactory` lang na bahala gumawa ng quest objects. The screen only needs to call:
QuestFactory.createQuest(type)

Mas okay ito because:
- Isang place lang ang responsible for creating quests.
- Hindi na kailangan malaman ng screen paano ginagawa yung bawat quest.
- If may bagong quest type, update lang sa factory.
- Mas organized and easier to extend.
- Mas mababa ang chance of repeated or inconsistent code.

Basically, the Factory Pattern works here because Mystery Match Quest has different quest types, and those quest types should be created in a **centralized and consistent** way.

---

### v. Pseudocode
``` code
CLASS IcebreakerQuest:
FUNCTION start():
RETURN "Answer a fun icebreaker question."
CLASS CampusSpotQuest:
FUNCTION start():
RETURN "Choose your favorite UPV campus spot."
CLASS PersonalityQuest:
FUNCTION start():
RETURN "Answer a personality-based prompt."
CLASS StudyHabitQuest:
FUNCTION start():
RETURN "Compare your study habits with your match."
CLASS QuestFactory:
FUNCTION createQuest(type):
IF type == "icebreaker":
RETURN new IcebreakerQuest()
ELSE IF type == "campus_spot":
RETURN new CampusSpotQuest()
ELSE IF type == "personality":
RETURN new PersonalityQuest()
ELSE IF type == "study_habit":
RETURN new StudyHabitQuest()
ELSE:
RETURN error "Unknown quest type"

MAIN PROGRAM:
selectedQuestType = "campus_spot"
quest = QuestFactory.createQuest(selectedQuestType)
DISPLAY quest.start()
```
---


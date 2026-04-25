# UPV Dating App with a Twist: Design Pattern Implementation

## Table of Contents

- [A. App Summary](#a-app-summary)
- [B. Design Pattern Implementation](#b-design-pattern-implementation)
  - [Pattern 1: Creational - Factory Pattern](#pattern-1-creational---factory-pattern)
    - [i. Name of Pattern](#i-name-of-pattern)
    - [ii. Concept](#ii-concept)
    - [iii. Visual Diagram](#iii-visual-diagram)
    - [iv. Why it Works](#iv-why-it-works)
    - [v. Pseudocode](#v-pseudocode)
  - [Pattern 2: Behavioral - Observer Pattern](#pattern-2-behavioral---observer-pattern)
    - [i. Name of Pattern](#i-name-of-pattern-1)
    - [ii. Concept](#ii-concept-1)
    - [iii. Visual Diagram](#iii-visual-diagram-1)
    - [iv. Why it Works](#iv-why-it-works-1)
    - [v. Pseudocode](#v-pseudocode-1)
  - [Pattern 3: Structural - Adapter Pattern](#pattern-3-structural---adapter-pattern)
    - [i. Name of Pattern](#i-name-of-pattern-2)
    - [ii. Concept](#ii-concept-2)
    - [iii. Visual Diagram](#iii-visual-diagram-2)
    - [iv. Why it Works](#iv-why-it-works-2)
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

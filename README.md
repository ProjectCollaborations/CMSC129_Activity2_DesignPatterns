# UPV Dating App with a Twist: Design Pattern Implementation

## Understanding Patterns Through a UPV Dating Application

## Table of Contents

- [Introduction](#introduction)
- [What are Design Patterns?](#what-are-design-patterns)
- [Our Example: UPV Dating App](#our-example-upv-dating-app)
- [Pattern 1: Factory Pattern](#pattern-1-factory-pattern)
- [Pattern 2: Observer Pattern](#pattern-2-observer-pattern)
- [Pattern 3: Adapter Pattern](#pattern-3-adapter-pattern)
- [Best Practices](#best-practices)
- [Summary](#summary)

---

## Introduction

Design patterns are reusable solutions to common problems in software design. They are not full programs or exact code templates. Instead, they are proven ways of organizing code so that an application becomes easier to maintain, extend, and understand.

In this project, the design patterns are applied to a fictional **UPV Dating App with a Twist**. The goal is to demonstrate how one **Creational**, one **Behavioral**, and one **Structural** design pattern can be used in a real application idea.

The three patterns used are:

| Pattern Category | Pattern Used | Main Purpose |
| --------------- | ------------ | ------------ |
| **Creational** | **Factory Pattern** | Creates different types of objects without scattering creation logic |
| **Behavioral** | **Observer Pattern** | Notifies multiple parts of the system when an important event happens |
| **Structural** | **Adapter Pattern** | Allows incompatible systems or data formats to work together |

---

## What are Design Patterns?

**Design patterns** are common solutions to recurring software design problems. They help developers avoid messy code by giving them a structured way to solve problems that usually appear as an application grows.

When developers are still starting out, they may solve problems by writing direct code everywhere. However, as the system becomes larger, this can lead to repeated logic, tightly connected components, and code that is difficult to update.

Design patterns help solve these problems by making the code:

- **More maintainable** - easier to update and fix
- **More reusable** - useful in different parts of the system
- **More scalable** - easier to extend when the app grows
- **More organized** - each class or component has a clearer responsibility
- **Easier to communicate** - developers can use shared terms like Factory, Observer, and Adapter

### The Three Pattern Categories Used in This Project

| Category | Purpose | Pattern Used in This App |
| -------- | ------- | ------------------------ |
| **Creational Pattern** | Focuses on how objects are created | **Factory Pattern** |
| **Behavioral Pattern** | Focuses on how objects communicate and react | **Observer Pattern** |
| **Structural Pattern** | Focuses on how objects or systems are connected | **Adapter Pattern** |

---

## Our Example: UPV Dating App

Throughout this guide, we will apply design patterns to a dating application called **IskoMatch**.

```text
UPV Dating App
├── Mystery Match Quest Creation
│   └── Factory Pattern
├── New Match Event System
│   └── Observer Pattern
└── Campus Event and Date Idea Integration
    └── Adapter Pattern

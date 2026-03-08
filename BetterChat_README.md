
# BetterChat (Optimized Fork)

**Author:** SeesAll  
**Based on original plugin by:** LaserHydra  
**Original Project:** Better Chat for uMod/Oxide

## Overview
This repository contains a lightly optimized fork of the popular **BetterChat** plugin originally created by LaserHydra for Rust servers running **uMod/Oxide**.

The goal of this revision is **not to change functionality**, but to improve performance and maintainability while preserving full compatibility with existing BetterChat configurations and plugins that rely on its API.

This version is intended to behave exactly like the original plugin while reducing unnecessary overhead and improving code stability.

---

# Why This Fork Exists

BetterChat is widely used across Rust servers, but the original plugin includes some areas that can create unnecessary allocations or redundant work during heavy chat usage.

The goals of this fork were:

* Maintain **100% compatibility**
* Improve **performance efficiency**
* Reduce **memory allocations**
* Clean up **code structure**
* Improve **error handling and safety**
* Maintain compatibility with plugins using the **OnBetterChat hook**

---

# Key Improvements

## 1. Reduced Garbage Allocation
Several areas of the plugin previously created temporary lists, arrays, or dictionaries repeatedly during chat processing.

These were optimized to:

* reuse structures where possible
* reduce unnecessary conversions
* avoid repeated LINQ allocations in hot paths

This reduces GC pressure on busy servers.

---

## 2. Safer Data Loading
Improved error handling when loading chat group data files.

If the data file becomes corrupted or missing, the plugin now safely initializes default structures instead of throwing errors.

---

## 3. Improved Player Lookup
Player search logic used in admin commands was cleaned up to:

* reduce redundant list creation
* improve string comparisons
* reduce unnecessary LINQ usage

This improves responsiveness for large servers.

---

## 4. Improved Chat Processing Loop
Chat dispatch loops were slightly optimized to reduce repeated checks and improve clarity.

No behavior changes were introduced.

---

## 5. Code Maintainability Improvements

General refactoring included:

* safer null handling
* improved readability
* simplified logic in several helper methods
* reduced repeated code

These changes make future maintenance easier.

---

# Compatibility

This fork remains fully compatible with:

* Existing **BetterChat configs**
* Existing **BetterChat data files**
* Plugins using:
  * `OnBetterChat`
  * `API_GetFormattedMessage`
  * `API_GetFormattedUsername`
  * other BetterChat API methods

No configuration changes are required.

---

# Intended Use

This version is intended for server owners who want:

* the original BetterChat behavior
* improved stability
* slightly lower runtime overhead
* cleaner maintained code

---

# Credits

Original plugin by **LaserHydra**.

This repository simply maintains a performance‑focused revision while preserving the original design and functionality.

Huge thanks to LaserHydra for creating one of the most widely used chat plugins in the Rust server ecosystem.

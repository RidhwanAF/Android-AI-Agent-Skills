---
name: android-testing
description: "Token-efficient unit and UI test generation for ViewModels, UseCases, Repositories, and Compose UI."
---

# Android Testing SOP (Token-Efficient)

## ViewModel Tests
- Test UI state emissions with `Turbine` on `StateFlow`.
- Replace `Dispatchers.Main` with `StandardTestDispatcher()` using a JUnit test rule.

## UseCase & Repository Tests
- Test success and failure outcomes using `MockK` mocks or fake repository implementations.
- Verify data transformations between Data, Domain, and UI layers.

## Compose UI Tests
- Use `createComposeRule()` or `createAndroidComposeRule<ComponentActivity>()`.
- Find nodes via `onNodeWithText()`, `onNodeWithContentDescription()`, perform actions with `performClick()`, and assert with `assertIsDisplayed()`.

## Structure
- Unit tests in `src/test/`, instrumented UI tests in `src/androidTest/`. Append `Test` to class names.

## Clean Kotlin Test Code & Latest Syntax
- **Concise One-Liners:** Prefer single-expression test helpers, one-liner assertions (`assertEquals(expected, actual)`), and compact MockK stubs (`coEvery { repo.get() } returns Result.Success(data)`).
- **Latest Kotlin 2.x:** Use `data object` for test states, `sealed interface`, and `kotlin.time.Duration` for virtual clock advancing.

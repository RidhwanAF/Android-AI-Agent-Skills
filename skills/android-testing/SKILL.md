---
name: android-testing
description: Directs automated unit test generation for ViewModels, UseCases, Repositories, and Compose UI components.
---

# Automated Test Generation SOP

Trigger this skill whenever asked to "test", "write unit tests", or verify feature execution.

## Clean Kotlin Test Code & Latest Syntax (Mandatory)
- **Concise One-Liners:** Prefer single-expression test helpers, one-liner assertions (`assertEquals(expected, actual)`), and compact MockK stubs (`coEvery { repo.get() } returns Result.Success(data)`). Avoid ceremony and boilerplate.
- **Latest Kotlin 2.x Features:** Use `data object` for mock UI/event states, `sealed interface` for test state hierarchies, and `kotlin.time.Duration` for virtual time advancement (`testDispatcher.scheduler.advanceTimeBy(1.seconds)`).

## ViewModel Testing
- Test UI State emissions using `Turbine` for `StateFlow` collection.
- Inject `MainDispatcherRule` with `StandardTestDispatcher()` or `UnconfinedTestDispatcher()` to control coroutine execution.

## UseCase & Repository Testing
- Test both happy path and exception scenarios using `MockK` mocks or fake repositories.
- Verify exact state transformations between Data, Domain, and Presentation models.

## Compose UI Testing
- Use `createComposeRule()` or `createAndroidComposeRule()` for component tests.
- Test user interactions, recompositions, and assertions using `onNodeWithText()`, `performClick()`, and `assertIsDisplayed()`.

## File Naming & Organization
- Place unit tests in `src/test/` and UI tests in `src/androidTest/` matching the package structure.
- Append `Test` to target classes (e.g., `LocationViewModelTest.kt`).
# Jennylicious PWA V0.15.1 – Cooking Session Persistence

Built on the successfully tested V0.15.0.

Additional persistence:
- active cooking recipe
- selected cooking servings
- completed cooking steps
- active kitchen timers
- timer end timestamps, so remaining time is recalculated after reopening

When Jennylicious reopens during an unfinished cooking session, it returns to cooking mode with the previous progress. Active timers are recreated from their saved end timestamps.

All V0.15 recipe, image, weekly plan, shopping and cooking-history persistence remains unchanged.

Test:
1. Start cooking a recipe.
2. Complete one or more steps.
3. Change portions if desired.
4. Start a short timer.
5. Fully close Jennylicious while the session is still active.
6. Reopen it.
7. Verify cooking mode, completed steps, portions and timer are restored.
8. Finish cooking and verify the normal cook-history entry still works.

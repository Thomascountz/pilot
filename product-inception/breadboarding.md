# Breadboarding

Breadboarding is a term created by Basecamp in their book [_Shape Up_](https://basecamp.com/shapeup/).

{% embed url="https://basecamp.com/shapeup/1.3-chapter-04\#breadboarding" %}

**Breadboarding** in software product design is a borrowed term from electrical engineering where circuit designers use a tool called a breadboard to build temporary circuits for testing/prototyping.

In the same way, breadboarding affords software designers a component-based apporach to documenting user-flow prototypes without the distraction of UI design.

The three components of breadboarding are:

1. **Places**: _"These are places you navigate to, like screens, dialogs, menus that pop up"_. I think of these as part of the "Given" in behavior-driven design user stories. For example: "given that Sallie is logged in on her profile page." 
2. **Affordances**: _"These are things the user can act on, like buttons and fields."_ All of the things that our app user can interact with. Basecamp makes a note that interface copy is included in this. I think of this as the "When" part of a user story. For example: "when a user reads 'This action cannot be undone' and clicks 'Confirm'."
3. **Connection Lines:** _"These show how the affordances take the user from place to place."_ This is the "Then" of user stories: what happens after the user interacts with an _affordance_. In Basecamp nomenclature, these lead to a new _place_.


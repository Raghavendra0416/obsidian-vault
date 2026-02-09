How can we avoid writing a same long Inline CSS over and over for same element in different places of webpage or same CSS over and over for same element in in different places of webpage?
Ans:
We can use the below concepts:
1. We can use "Components" concept. Where we create Different components for `NavBar`, `SideBar`, Footer etc..
2. We can use "Directives" - "`@apply`" :- will apply tailwind CSS to CSS. "`@layer`" :- we can create custom styles for base components and utilities. "`Base`" :- apply styles globally to our project.
3. We can "Utilities" - Atomic styles for individual properties like padding, margins, typography etc..


Instead of using JS for styling, we can Tailwind for styling, by using Directives, Utilities.
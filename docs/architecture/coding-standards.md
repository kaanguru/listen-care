# Coding Standards

- **Style & Linting**: We will use the official **Kotlin style guide**. **Detekt** will be used for static analysis, configured to encourage functional programming paradigms.
- **Immutability**: Prefer `val` over `var`. Functions must accept and return immutable collection types.
- **Composition Over Inheritance**: Favor composition. Classes will remain `final` by default.
- **Responsive Design**: For V1, the application will target portrait mode only. Full support for landscape and tablet layouts is a post-MVP enhancement.

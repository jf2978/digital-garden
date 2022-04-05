- ## [Link](https://www.educative.io/courses/grokking-the-system-design-interview)
- # Notes
    - SDIs are particularly important interviews because they demonstrate your ability to design, understand (and presumably implement) complex systems and your thought process
    - Basic steps/formula that applies to designing systems during SDIs
        - **Clarify requirements**: you're not gonna design a robust, full-featured system, so just ask what they're looking for
        - **Estimate the scope**: similar to clarifying requirements, except asking questions around traffic/load/amount of data and then showing confidence around what that does to scope of the system
        - **Design the API**: outline method signatures that do the things you're designing for
        - **Design the Data Models**: talk about structure of the data tables (fields & objects we will care about)
        - **High-level design**: boxes and arrows
        - **Detailed design**: zoom into a handful of the components and talk about technical tradeoffs associated
        - **Identify and resolve bottlenecks**: can the system fail gracefully? any key parts we want to monitor/alert on? 
    - ## Designing TinyURL
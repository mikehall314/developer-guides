## Introduction

A code review is a process where someone other than the author of a piece of
code examines that code. The purpose of code review is to maintain the quality
of our code and our products.

Code reviews should look at:

- **Design**: Is the code well-designed and appropriate for your system?
- **Functionality**: Does the code behave as the author likely intended? Is the
  way the code behaves good for its users?
- **Complexity**: Could the code be made simpler? Would another developer be
  able to easily understand and use this code when they come across it in the
  future?
- **Tests**: Does the code have correct and well-designed automated tests?
- **Naming**: Did the developer choose clear names for variables, classes,
  methods, etc.?
- **Comments**: Are the comments clear and useful?
- **Documentation**: Did the developer also update relevant documentation, if
  any?

# How to do a code review

The pages in this section contain recommendations on the best way to do code
reviews, based on long experience. All together they represent one complete
document, broken up into many separate sections. You don't have to read them
all, but many people have found it very helpful to themselves and their team to
read the entire set.

- [The Standard of Code Review](standard.md)
- [What to Look For In a Code Review](looking-for.md)
- [Navigating a PR in Review](navigate.md)
- [Speed of Code Reviews](speed.md)
- [How to Write Code Review Comments](comments.md)
- [Handling Pushback in Code Reviews](pushback.md)

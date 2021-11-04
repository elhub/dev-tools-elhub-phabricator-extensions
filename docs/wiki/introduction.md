# Introduction

The devxp modules are intended to simplify and streamline development work at Elhub A/S and ensure all developers
have relatively consistent development environments. They are also intended to help improve security of developer PCs,
by making it simple to maintain and keep up to date the various software on these boxes.

## Requirements Overview

**Main features**
* Simplify installation of required software
* Installs all packages required for development
* Make updating and maintaining software as simple as possible

## Quality Goals

All devxp modules should follow the
[Software Quality Goals](https://confluence.elhub.cloud/display/EW/Software+Quality+Goals) of Elhub. In addition,
it has the following quality goals.

| ID  | Quality | Motivation |
| --- | ------- | ---------- |
| SQ1 | Simple to install | The devxp module must be easy to install and update. |

## Architecture Constraints

All devxp modules should follow the
[Software Architecture Principles](https://confluence.elhub.cloud/display/EW/Software+Architecture+Principles) of Elhub.
In addition, it should follow the following:

### Technical Constraints

| ID  | Constraint | Background/Motivation |
| --- | ---------- | --------------------- |
| TC1 | InTune Platform | Must function within the constraints of the Statnett Windows InTune platform. |

### Organizational Constraints

| ID  | Constraint | Background/Motivation |
| --- | ---------- | --------------------- |
| OC1 | Team       | Maintained by the @elhub/tools team. |

### Conventions

No special conventions.

## Stakeholders

The following lists the most important stakeholders for this module.

| Role/Name  | Goal/Boundaries |
| ---------- | --------------- |
| Developers | Developers who are the users of the various devxp modules. |
| Statnett IT Support | Who have the responsibility for delivering and maintaining InTune PCs |

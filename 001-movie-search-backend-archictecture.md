## Title
ADR 001: Movie Search - Backend Architecture

## Context
Movie Search application should have a architecture in order to distribute content. 

## Decision

The decision about architecture of communication with APIs and structure to distribute content via Blog is descripted below.

### 1. Movie Search Backend

Main function:
Searches for movies in the local IMDb database and allows you to favorite them.

Database:
Uses local MongoDB due to the large volume of data (690k documents).

### 2. Movie Search Backend Blog

**Main function:**
Distribute previously generated blog posts.

**Database:**
Uses Mongo Atlas for remote storage, enabling:

- Querying via APIs or via the frontend.
- Storing posts for display.

**Hosting:**
Heroku, with integration with Mongo Atlas.


### Flow between applications
Data generation and consumption (communication):

Movie Search Backend generates posts in the required format and automatically send the data to the Movie Search Backend Blog (via API).
Movie Search Backend Blog can consume the API.


POST /search → Searches for movie blogposts in Blog.

GET /<tconst> → Movie blogpost for a certain movie. Identified through IMDb universal code (= tconst parameter, unique for every movie in IMDb).


## Status
Proposed

## Consequences
Allow to distribute a consolidated pattern across Movie Search endpoints and all connected client APIs.

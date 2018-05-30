# Select Entity by id

## Purpose

- Make a selector which you can easily use with ActivatedRoute, relational search, etc.
- To show exemplify that you can just create a function that returns a createSelector.

## Description

Sometimes you need to select one entity from the collection and follow up on related changes.

Related discussion on Redux reselect GitHub issues https://github.com/reduxjs/reselect/issues/100

## Recipe

```typescript

export const {
  // select the dictionary of user entities
  selectEntities: getBookEntities,

  // select the array of users
  selectAll: getAllBooks,

  // select the array of user ids
  selectIds: getBookIds,

  // select the total user count
  selectTotal: getBookTotal,
} = fromRegion.adapter.getSelectors(getBookState);

export const getBookById = ( bookId ) => createSelector(
  getBookEntities,
  ( bookEntities ) => {
    return bookEntities[bookId];
  }
);
```

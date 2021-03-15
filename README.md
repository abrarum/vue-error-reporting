# Tasks achieved

_frontend_

-   [x] Write a UI that allows the operator to:
    -   [x] have an "nice" overview of all errors, it should show `unresolved`, then `resolved` and then `backlog` errors
        
        > I chose a fixed sidebar quick nav for destructuring the error types. The design choice is based on UX for quick sorting out errors logs instead of endless scrolling.

    -   [x] see the `text` and `code` of each error

        > Based on a table layout in which each column represents the related content to each error including `text`, `code` and `status`.

    -   [x] resolve each individual `unresolved` error by clicking an individual button
    -   [x] unresolve each individual `resolved` error (e.g., when an error was set to `resolved` by mistake) by clicking an individual button
    -   [x] move an individual backlog error to the bottom of the `unresolved` list of displayed errors, by clicking an individual button

        > Each category has a set of buttons to resolve, unresolve or backlog the error accordingly.

    -   [x] undo his last action. E.g., if he resolved an unresolved error, an `undo` functionality enables him to move it back into the unresolved list of 
    errors. This should work between all lists for _ only the last_ action of a user

        > Undo works for the last action performed by the user on a specific error category. The action is based off the user's choice to either click a central undo button at the top (not fixed position) or by keystrokes: ctrl+z.


_other comments_

> Added an additional 'status' property in the api for ease of use.

> Transitions added on updation of rows (append/delete). Can be switched off by updating the data property: `'row_trans: false'`.
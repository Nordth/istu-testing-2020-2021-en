# Task 2

For given code:
1) Create [control flow graph](https://en.wikipedia.org/wiki/Control-flow_graph)
2) Create input dataset, that allows to visit all nodes in this graph

```
// myId - id of current user
// applicationStatus - status: NEW, EDIT, AWAIT, CANCELED, COMPLETED
// applicationLockedBy - user who lock application or null
// applicationIsChanging - true/false
// resultType - "complete", "cancel" or null
function getMenu ( myId, applicationStatus, applicationLockedBy, applicationIsChanging, resultType  ){

    const locked_by_others = applicationLockedBy && applicationLockedBy !== myId;
    const locked_by_me = applicationLockedBy && applicationLockedBy === myId;

    const submit = { title: 'cancel', icon: 'icon-submit'}
    const cancel = { title: 'cancel', icon: 'icon-cancel'}
    const history = { title: 'cancel', icon: 'icon-history'}
    const print = { title: 'cancel', icon: 'icon-print'}
    const requestChange = { title: 'Request change', icon: 'icon-edit' }
    const lock = { title: 'Lock', icon: 'icon-lock', disabled: !locked_by_me  }
    const unlock = { title: 'Unlock', icon: 'icon-unlock', disabled: locked_by_me}
    const openResultAbort = { title: 'Отклонить', icon: 'icon-cancel' }
    const openResultResult = { title: 'Согласовать', icon: 'icon-check' }
    const lockedInfo = { type: 'lock'};

    let left = [history, print];
    let right;

    if (locked_by_others){
        right = [lockedInfo];
    }
    else {
        if (!locked_by_me){
            right = [lock]
        }
        else if (applicationIsChanging) {
            right = [cancel, requestChange];
        }
        else if (resultType){
            right = [
                unlock,
                resultType,
                submit
            ]
        }
        else {
            right = [unlock]
            if (applicationStatus !== AWAIT){
                right.push(openResultAbort)
                right.push(openResultResult)
            }
        }
    }

    return [left, right]
}
```

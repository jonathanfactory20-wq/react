
## Input

```javascript
import {memo} from 'react';
import {Stringify} from 'shared-runtime';

export const MemoFoo = memo(Foo);
export function Foo({prop1, prop2}) {
  'use memo';
  return <Stringify prop1={prop1} prop2={prop2} />;
}

export const FIXTURE_ENTRYPOINT = {
  fn: eval('Foo'),
  params: [{prop1: 1, prop2: 2}],
};

```

## Code

```javascript
import { c as _c } from "react/compiler-runtime";
import { memo } from "react";
import { Stringify } from "shared-runtime";

export const MemoFoo = memo(Foo);
export function Foo(t0) {
  "use memo";
  const $ = _c(3);
  const { prop1, prop2 } = t0;
  let t1;
  if ($[0] !== prop1 || $[1] !== prop2) {
    t1 = <Stringify prop1={prop1} prop2={prop2} />;
    $[0] = prop1;
    $[1] = prop2;
    $[2] = t1;
  } else {
    t1 = $[2];
  }
  return t1;
}

export const FIXTURE_ENTRYPOINT = {
  fn: eval("Foo"),
  params: [{ prop1: 1, prop2: 2 }],
};

```
      
### Eval output
(kind: ok) <div>{"prop1":1,"prop2":2}</div>
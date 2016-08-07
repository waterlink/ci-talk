# Continuous Integration Training

TDD Screencast #6



<img src="../my-presentation-template/me.jpeg" class="photo-me">

## Oleksii Fedorov

Software Craftsperson

@waterlink000



## Agenda

1. Continuous Integration
2. Check Out - Check In Cycle
3. Training Kata with Restrictions
4. Live Coding
5. Bottom Line



## Continuous Integration

Jenkins, Travis, etc. are not CI

They are build servers


### Integrating Continuously

Every few minutes

```bash
git push upstream master
```


### Why?

Avoid long-running feature branches and painful merges

And enable Continuous Delivery



## How often to integrate?


### TDD Red-Green-Refactor Cycle

1. Check Out
2. Red-Green-Refactor
3. Check In


Practically (git example):

```bash
git pull --rebase
```

One cycle of Red-Green-Refactor

```bash
git commit -m "..."
git pull --rebase
```

(Fix conflicts if any)

```bash
git push upstream master
```


### 3-5 minutes long

(on average)



## This is really hard

(at first)


### How can I train this?



## `Discard on RED` restriction

- Pick any TDD Kata
- Set up a timer to ring every 2 minutes
- Every time it rings, run tests:
  - `GREEN` -> proceed
  - `RED` -> discard any changes
- Commit only when `GREEN` at any time


### Tooling

```bash
# $ red
red() {
	git reset --hard
	git clean -df
}

# $ green Implement my new nice feature
green() {
	git add .
	git commit -m "$*"
}
```

(in bash)



## Matches 3 Kata

There is a field with gems of different colors. When player swaps two neighboring gems:

- 3 or more gems of the same color in row or column are destroyed, or
- swap is rejected if there are no such gems.

Gravity: When gems are destroyed, the gems placed on top of them are moved down to fill empty cells of the field.

This may result in more gems destroyed.


### Example:

```bash
RGRBB      RGR↓B      RGRGB      RGRGB      R↓↓↓B  ->  R...B
RBBGR  ->  RBB↑R  ->  RBBBR  ->  R***R  ->  R...R  ->  RGRGR
GGBRB      GGBRB      GGBRB      GGBRB      GGBRB  ->  GGBRB

          (swap)               (destr.)   (gravity)
```



## Demo




## Thanks

Twitter: [twitter.com/waterlink000](https://twitter.com/waterlink000)

Github: [github.com/waterlink](https://github.com/waterlink)

Blog: [tddfellow.com](http://tddfellow.com)

All TDD Screencasts: [bit.ly/tdd-screencasts](http://bit.ly/tdd-screencasts)

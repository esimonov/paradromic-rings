# Möbius strip dissections CLI

Paradromic rings are shapes created by cutting a Möbius strip across its width. This CLI can be used for computing their basic structural properties.

The main goal of the project was to explore Scheme's capabilities as a general purpose programming language. It's implemented in R5RS Scheme and uses SRFI-28 for string formatting.

The idea for a subject was inspired by Dr Tadashi Tokieda's course [Topology & Geometry](https://youtu.be/SXHHvoaSctc?si=9bXOmKjzHKfTlmgv).

## Why?

Some surprising properties show up when dissecting Möbius strips and similar structures.

```text
A mathematician confided
That a Mobius band is one-sided,
And you'll get quite a laugh,
If you cut one in half,
For it stays in one piece when divided.
```

![Cut along the centerline](/assets/Moebiusband-1s.svg)

When the strip is dissected off-center instead, the result may seem even stranger:

![Off-center cut](/assets/Moebiusband-2s.svg)

Let's use the CLI to verify what we've just seen!

```text
Let L and W denote the initial length and width of the strip, respecitively.

Enter the number of initial half-twists (or 'q' to quit) : 1
Enter D>=2 to mark the line 1/D along which the strip will be dissected (or 'q' to quit) : 2
---------
When dissecting a strip with 1 half-twist 1/2 way across its width, you get a single connected strip which is 2 times longer than the original one:

Length: 2L
Width: W/2
Number of half-twists: 4


---------

Let L and W denote the initial length and width of the strip, respecitively.

Enter the number of initial half-twists (or 'q' to quit) : 1
Enter D>=2 to mark the line 1/D along which the strip will be dissected (or 'q' to quit) : 3
---------
When dissecting a strip with 1 half-twist 1/3 way across its width, you get two linked strips, one of which is 2 times longer than the other:

Strip #1
Length: 2L
Width: W/3
Number of half-twists: 4

Strip #2
Length: L
Width: W/3
Number of half-twists: 1



---------

Let L and W denote the initial length and width of the strip, respecitively.

Enter the number of initial half-twists (or 'q' to quit) : q
Goodbye!
```

Basic santity check:

```text
Enter the number of initial half-twists (or 'q' to quit) : 0
Enter D>=2 to mark the line 1/D along which the strip will be dissected (or 'q' to quit) : 2
---------
When dissecting an untwisted strip 1/2 way across its width, you get two disconnected strips of the same length:

Strip #1
Length: L
Width: W/2
Number of half-twists: 0

Strip #2
Length: L
Width: W/2
Number of half-twists: 0
```

Basic insanity check:

```text
Enter the number of initial half-twists (or 'q' to quit) : 101
Enter D>=2 to mark the line 1/D along which the strip will be dissected (or 'q' to quit) : 7
---------
When dissecting a strip with 101 half-twists 1/7 way across its width, you get two linked strips, one of which is 2 times longer than the other:

Strip #1
Length: 2L
Width: W/7
Number of half-twists: 204

Strip #2
Length: L
Width: 5W/7
Number of half-twists: 101
```

Original image sources:

* [Cut along the centerline](https://commons.wikimedia.org/wiki/File:Moebiusband-1s.svg)
* [Off-center cut](https://commons.wikimedia.org/wiki/File:Moebiusband-2s.svg)

## How to run

Compile and run with [CHICKEN Scheme](https://call-cc.org/):

```sh
csc main.scm
./main
```

Or interpret without compilation:

```sh
csi main.scm
```

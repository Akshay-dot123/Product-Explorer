# Notes

> Fill this in as you work. This document is assessed alongside your code.

## Bugs I found

For each: what was wrong, **why** it was wrong, and how I fixed it.

1. The dependency array contains products. Inside the effect, call setProducts(data).This updates the products state, which immediately triggers the useEffect to run again. This creates an infinite loop of network requests.
Solution: Change the dependency array to an empty array []. SO here only once components runs.
2. Using 'any' type defeats the purpose of TypeScript. Change the state to useState<Product[]>([]) and type the parsed JSON as const data: Product[] = await res.json();
3. if (!product) return null;instantly mount and unmount components.
Solution: <AnimatePresence> detects when a child is removed from the React tree and delays the actual unmounting just long enough to play an exit animation.

## Features I completed

-

## Decisions

Anywhere I had to choose between options — and why I chose what I did.

-

## With more time

What I'd improve or add next.

-

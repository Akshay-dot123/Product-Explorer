# Notes

> Fill this in as you work. This document is assessed alongside your code.

## Bugs I found

For each: what was wrong, **why** it was wrong, and how I fixed it.

1. The dependency array contains products. Inside the effect, call setProducts(data).This updates the products state, which immediately triggers the useEffect to run again. This creates an infinite loop of network requests.
Solution: Change the dependency array to an empty array []. SO here only once components runs.
2. Using 'any' type defeats the purpose of TypeScript. Change the state to useState<Product[]>([]) and type the parsed JSON as const data: Product[] = await res.json();
3. if (!product) return null;instantly mount and unmount components.
Solution: <AnimatePresence> detects when a child is removed from the React tree and delays the actual unmounting just long enough to play an exit animation.
4. visibleProducts function in pages.tsx uses if pattern which only checks 1 thing at a time.
if (category !== "all") {
  return product.category === category;  // Only checks category
}
return product.title.includes(search);   // Only checks search
Solution: To work together we are changing code to match both category and search option both at once like this:
const matchesCategory = category === "all" || product.category === category;
const matchesSearch = product.title.toLowerCase().includes(search.toLowerCase());
return matchesCategory && matchesSearch;
5. Added helpful error state to the user when the request fails.
6. key={index} here key is tied to where the item is in the array (0,1, 2,3...), so if the array changes, the positions shift
Solution: key={product.id} here key is tied to what the item actually is (a unique identifier). Identity stays the same regardless of position
7. Removed the dynamic timestamp. This ensures the server and client generate the exact same initial HTML, preventing the mismatch.

## Features I completed

-

## Decisions

Anywhere I had to choose between options — and why I chose what I did.

-

## With more time

What I'd improve or add next.

-

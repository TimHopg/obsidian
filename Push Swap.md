#School42 #C_Language #todo 

_Stack A_ - populated with elements
_Stack B_ - begins empty

_sa_ (swap a) - swap first two elements in _Stack A_
	(does nothing if there are one or zero elements)
_sb_ (swap b) - swap first two elements in _Stack B_
	(does nothing if there are one or no elements)
_ss_ (swap swap) - _sa_ and _sb_ at the same time

_pa_ (push a) - push the first element from _Stack B_ onto _Stack A_
	(does nothing if _Stack B_ is empty)
_pb_ (push b) - push the first element from _Stack A_ onto _Stack B_
	(does nothing if _Stack A_ is empty)

_ra_ (rotate a) - Shift all elements of _Stack A_ up by one.
	The first element becomes the last one.
_rb_ (rotate a) - Shift all elements of _Stack B_ up by one.
	The first element becomes the last one.
_rr_ (rotate rotate) - _ra_ and _rb_ at the same time
_rra_ (reverse rotate a) - Shift all elements of _Stack A_ down by one.
	The las element becomes the first one.
_rrb_ (reverse rotate b) - Shift all elements of _Stack B_ down by one.
	The las element becomes the first one.
_rrr_ (reverse rotate rotate) - _rra_ and _rrb_ at the same time.

#### Parsing Data

Adjustments to `atoi` must be made so as not to accept input with alpha chars and not to consider a lone `+` or `-` as `0`. I received this number as a long that way I could interpret `INT_MIN - 1` and `INT_MAX + 1` as errors also.

Also duplicates must return an error. In all of these occurrences  the list/stack must be freed.
#### Approach 1 (Mechanical Turk)

- Works best with cyclical and doubly linked list and list with indexes.
- Also not especially 'algorithmic' as the name suggests. Named after a programmed chess automaton. Each step is hard coded more or less.

The goal of this approach is to create a sorted list in _B_ (_largest to smallest_) until three elements are left in _A_ and then...

A size of three can be sorted in 2 operations at worst. 1 at best.

| 1   | _sa_ | 3   | _ra_ | 1   |
| --- | ---- | --- | ---- | --- |
| 3   |      | 1   |      | 2   |
| 2   |      | 2   |      | 3   |
See more: [[Push Swap probability grid]]

Step 1 - push top two elements from  _A -> B_ .
These elements are non-discriminatory because we just need to have a max and min value for _B_.

Then calculate how many operations it would take to push each value into the correct position into _B_.

If our next number (_7_) is bigger than our largest number in _B_, _B_ might need to be rotated to ensure the new number is placed 1 position above the previous largest. This would be 2 operations. If no more efficient number is found (fewer than 2 operations) _7_ is pushed.

If an operation of cost 1 is found, do that because no operation will be cheaper.

Once B is sorted from _largest to smallest_ we can start add pushing from _B_ to _A_ but we must rotate _A_ until it's in the correct position to accept _B_ (until the element with the value immediately above _B_ is at the top of _A_).

Repeat until _B_ is empty.
Then rotate _A_ until smallest number is at the top.
#### Approach 2 (Best Friend)

While _A_ has more than 5 elements, pop the top element from _A_ if it is lower than the mean of the list. If it's not, rotate _A_.

When _A_ has five elements remaining, sort those five into ascending order:
- Hard code an algorithm to sort a list of three.
- To sort a list of four, rotate to get the smallest on top (check it's not already sorted) then pop to b and utilise three_sort.
- To sort a list of four, do the same thing. Rotate until the smallest is on the top (check it's not already sorted), pop to b and then utilise four_sort.

Now find the _best friend_ of each number in _b_.
Subtract each number in _A_ from the first number in _B_. Look for the lowest positive number.
Repeat to find the best friend of each subsequent number.
You're looking for the number in _A_ that is bigger but closest to each number in _B_.
This is because _A_ will be rotated and each number in _B_ will be pushed to the top on top of the number that is immediately above it. Maintaining the order of _A_.

| A   | B   | best friend |
| --- | --- | ----------- |
| 4   | 9   | 8 > 9       |
| 1   | 6   | 4 > 5       |
| 8   | 5   | 4 > 6       |

Next the cheapest of the best friend pairs are found by working out the cost of rotating each stack so they would both be on top. Shared operations are taken into consideration. i.e. if both numbers need positive rotations to get to the top, _rr_ will be used until one reaches it then _ra_ or _rb_ to finish the job. The same can be said for numbers near the bottom using _rrr_. If numbers are at either ends, they are usually more inefficient since they cannot share operations.

These best friends are stored in an array of a new structure(which can be freed on each iteration) since we know the length it will need to be (the length of _stack b_). Inside that struct, the data of _a_ and _b_, the cost of each of them to arrive to the top and also the total cost (include shared operations) is stored.

Rotating these friends can be complicated because it depends on whether they both require positive or negative rotations or if they require different rotations.

These best friend, rotate and push steps are repeated until _B_ is emptied.

The last step is just to rotate _A_ until the lowest number is at the top.

#### Checker
The checker takes a list of arguments which are parsed into the stack (using the same parsing function as used in the mandatory part). Checker returns Error if an error is encountered.
If the list is sorted, the prompt is returned.

Otherwise the program waits for operation instructions, separated by a newline. When all instructions have been entered (`Ctrl + D` EOF (end of file)) the checker returns `OK` if the list is sorted and `KO` if the instructions did not sort the list.
#### Tips 
- Adapted `atoi` must handle '`+`' and '`-`' (not treat as zero). Must not include letters etc.
- " " and "" should return an error
- Error must be on standard out (2)
- Test with many negatives or all negatives
- Checker: test for sorted list that doesn't match original list
- Checker: test for bad op instruction + (sorted list || list length shorter than original)
- _Checker: Make sure the sorted list is the same length as the original list_

The following is a handy line to generate numbers between -1000 and -500 in a random order. Add `wc -l` to count number of operations
```ARG=`echo {-1000..-500}$'\n' | sort -R | tr "\n" " "` ; ./push_swap $ARG```
#### References
[Best Friend (Duarte3333)](https://github.com/duarte3333/Push_Swap)
[Mechanical Turk (Medium)](https://medium.com/@ayogun/push-swap-c1f5d2d41e97)
[Mechanical Turk (Ayogun)](https://github.com/ayogun/push_swap)
[Visualiser](https://github.com/o-reo/push_swap_visualizer)
[GeMartin99 Tester](https://github.com/gemartin99/Push-Swap-Tester/tree/master) - this expects `""` and `" "` to return `Error` (I consider this the correct behaviour)
[Leo Fu Tester](https://github.com/LeoFu9487/push_swap_tester) - this expects `""` and `" "` to return prompt

_2024-06-06 12:09_
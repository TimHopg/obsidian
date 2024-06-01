#Algorithms 

Swapping numbers if out of order

[[Big O notation]] On² (Ωn Θn²)


```c
void	swap(int *a, int *b) // swaps ints
{
	int	temp;

	temp = *a;
	*a = *b;
	*b = temp;
}

void	ft_sort_int_tab(int *tab, int size) // takes pointer to first array and array size
{
	int	i; 
	int	j;

	i = 0;
	while (i < size - 1) // while i is less than the size of the array
	{
		j = 0; // to look at the first item again
		while (j < size - i - 1) // while j is less than number of iterations. after each iteration, the largest number will be correct at the right side.
		{
			if (tab[j] > tab[j + 1]) if first two elements are out of order
			{
				swap(&tab[j], &tab[j + 1]);
			}
			j++;
		}
		i++; // 1 is added to i on each iteration through the loop
	}
}
```
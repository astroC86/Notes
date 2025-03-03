

In your code the inner product is computed only for indices that are neither equal to $j$ nor equal to $lorder(i+1)-1$. Notice that for a fixed $i$ the inner product

$$\text{aux} = \prod_{\substack{m=0 \\ m\neq j,\;m\neq lorder(i+1)-1}}^{mporder}\frac{(xi\_p - xi(m+1))}{(xi(lorder(i+1)) - xi(m+1))}$$

can be viewed as the full product over all $m$ (except $m=lorder(i+1)-1$) divided by the missing factor corresponding to $m=j$. In other words, if you define

$$P = \prod_{\substack{m=0 \\ m\neq lorder(i+1)-1}}^{mporder}\frac{(xi\_p - xi(m+1))}{(xi(lorder(i+1)) - xi(m+1))}$$

then for each allowed $j$ (i.e. $j\neq lorder(i+1)-1$) you have

$$\text{aux} = \frac{P}{\frac{(xi\_p - xi(j+1))}{(xi(lorder(i+1))-xi(j+1))}} = P \cdot \frac{(xi(lorder(i+1))-xi(j+1))}{(xi\_p - xi(j+1))}\,.$$

Thus, the term

$$\frac{1}{(xi(lorder(i+1))-xi(j+1))}\times \text{aux}$$

simplifies to

$$\frac{P}{(xi\_p - xi(j+1))}\,.$$

So, the sum over $j$ becomes

$$dl\_ip(i+1) = P \sum_{\substack{j=0 \\ j\neq lorder(i+1)-1}}^{mporder}\frac{1}{(xi\_p - xi(j+1))}\,.$$

Now, instead of using if conditions to skip the index $lorder(i+1)-1$, you can split your loops into two ranges: one for indices below $lorder(i+1)-1$ and one for indices above it. For example, here's one way to rewrite the code:

```fortran
do i = 0, mporder
   ! Compute product P over m ≠ lorder(i+1)-1 using two loops
   P = 1.0d0
   ! Loop over m from 0 to lorder(i+1)-2
   do m = 0, lorder(i+1)-2
        P = P * (xi_p - xi(m+1))/(xi(lorder(i+1))-xi(m+1))
   end do
   ! Loop over m from lorder(i+1) to mporder
   do m = lorder(i+1), mporder
        P = P * (xi_p - xi(m+1))/(xi(lorder(i+1))-xi(m+1))
   end do

   ! Now, compute the sum over j for allowed indices
   sum = 0.0d0
   ! Loop over j from 0 to lorder(i+1)-2
   do j = 0, lorder(i+1)-2
        sum = sum + 1.0d0/(xi_p - xi(j+1))
   end do
   ! Loop over j from lorder(i+1) to mporder
   do j = lorder(i+1), mporder
        sum = sum + 1.0d0/(xi_p - xi(j+1))
   end do

   dl_ip(i+1) = P * sum
end do
```

Q1: How does affect the numerical accuracy of the code?
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2NjYzOTI2MF19
-->
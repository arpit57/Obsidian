Lets start with vectors,vectors can be treated as list of numbers,a point in space or an object with both magnitude and direction.We will understand the geometrical interpretation of linear algebra in next part,as of now,lets define vector as an element V ∈R^n.

> Vector V can be defines as an element of n dimensional coordinate system i.e V∈R^n.

So for 2D plane [x,y] is general form of vector,for 3D it’s [x,y,z] as so on for dimensions.

Transpose of vector(V^T) = vector is represented in column form and it’s transpose is the row representation of same.

![](https://miro.medium.com/max/286/1*YpHXzcVVycanF8HLZnsH2A.png)

**vector transpose**

> A matrix M can be defined as an element M∈R^(mxn) i.e m collection of n dimensional vectors taken as row of matrix having dimension mxn.

![](https://miro.medium.com/max/374/1*IOAm6GrmT-CVZxby9DxJ6A.png)

matrix of dim mxn

Transpose of matrix:-

![](https://miro.medium.com/max/453/1*_Vq3ET4DEA6wlYN9EQIJoQ.png)

matrix transpose

We can consider vector as a single dimensional array and matrix as an 2 dimensional array.

In machine learning we may need multidimensional array as form of data to perform computation and operation which we refer as tensor.

> Tensor is the generalization of vectors and matrices mostly understood as multidimensional array.

Vector is 1st order or single dimensional tensor while matrix is 2D tensor.

![](https://miro.medium.com/max/473/1*PMYsLyEuaxf2nhho100YPA.jpeg)

**elements in linear algebra**

We will now study properties and operations of 1D(vector) and 2D(matrix) tensor and that can be generalized to all higher dimensions.

![](https://miro.medium.com/max/625/1*MQIAAntN5tYgKEDNTcpZmg.png)

**multi-dimensional tensor**

# **Operations on vectors**

**operations with scalar:-** any operation with scalar is performed with every element of vector.

![](https://miro.medium.com/max/640/1*GVwN83iC3rNLB6ua_A0r9Q.png)

**Addition and Subtraction:-** vectors of same dimension are added and subtracted element-wise.

![](https://miro.medium.com/max/356/1*gy7sTG7NpyiZg-EtwDfaJw.png)

**Dot product/Inner product :-** dot product and inner product are two different things in mathematics but will be same in our context.It is the summation of element-wise product of two vectors of same dimension.

![](https://miro.medium.com/max/524/1*R6fUTQ3rNeUcDBFeVGu5RQ.png)

**dot product of vectors**

**Outer product:-** element wise scaling of one vector by another that results in matrix is called outer product

![](https://miro.medium.com/max/623/1*Xy9_RW5dWkL5mS7cz-_vlA.png)

**outer product of vectors**

# Operations on matrices

**matrix matrix multiplication:-** It can be regarded as inner products of every row on 1st matrix with columns of 2nd matrix.

![](https://miro.medium.com/max/625/1*ajFI2uF1WH3iShjxbCWOeg.jpeg)

**inner product explanation of matrix multiplication**

It can also be defined as sum of all outer products of row of matrix 1 with column of matrix 2.

![](https://miro.medium.com/max/549/1*ixNxbXSjmYI7_sfnp30Xeg.png)

**outer product intuition of multiplication**

Both intuition of matrix multiplication gives same result respecting the norms of mathematics.

**Row Reduction/Gaussian Elimination:-** Some certain operations can be produced with rows of the matrices that may change the matrix but doesn’t changes the interpretation of data or equation represented.These techniques are generally used to solve system of linear equations and inverse of matrix.

![](https://miro.medium.com/max/875/1*iTm7DzQvtsm8uO9KhT9J0Q.jpeg)

# Types and representation of matrix

**Diagonal Matrix =** A matrix with all elements except diagonal being 0 is called diagonal matrix.

![](https://miro.medium.com/max/364/1*WEnHkTmcxyCjDXONj_SQug.png)

**diagonal matrix**

**Lower Triangular and upper triangular matrix =** A matrix with all elements below diagonal being 0 is called upper triangular and if all elements above diagonal is 0 is called lower triangular matrix.

![](https://miro.medium.com/max/414/1*S4mrEEWexPbA20D_XaZZgA.png)

**Identity matrix =** Diagonal matrix with all element one having property of A.I = A is called identity matrix.

![](https://miro.medium.com/max/360/1*wjUibs0dWW8-3_1QxdLTrA.png)

**Identity matrix**

**Symmetric matrix =** Matrix whose transpose is same to original matrix.

**Skew-symmetric matrix =** matrix whose transpose is equal to negative of original matrix.

![](https://miro.medium.com/max/386/1*abNRjzUkdZoiWkVSi5Q63A.png)

**Row Echelon form =** A matrix which satisfies following properties is called in row echelon form.

-   The first non-zero number from the left (the “[leading coefficient](https://www.calculushowto.com/leading-coefficient-definition-test/#leading)“) is always to the right of the first non-zero number in the row above.
-   Rows consisting of all zeros are at the bottom of the matrix.

**Reduced Row Echelon form =** A matrix which satisfies following properties is called in reduced row echelon form.

-   The first non-zero number in the first row (**the leading entry**) is the number 1.
-   The second row also starts with the number 1, which is further to the right than the leading entry in the first row. For every subsequent row, the number 1 must be further to the right.
-   The leading entry in each row must be the only non-zero number in its column.
-   Any zero rows are placed at the bottom of the matrix.

![](https://miro.medium.com/max/575/1*u_EFuinZwtJqUDGBTykYpQ.jpeg)

The matrix can be converted to row echelon or reduced row echelon with the help of **row reduction method** discussed above.

![](https://miro.medium.com/max/875/1*LNmciGgnXMqD4RaGGJy6TA.png)

# System of linear equations

we all know about linear equations

**a0 + a1x1 + …** **+ anxn = c**

This is the system of m linear equation of n variables shown below

![](https://miro.medium.com/max/450/1*fs7gNHIdVKhBFumKl3qF-A.png)

**m linear equations of n variables**

If all the bi’s are 0, it is called homogeneous system of linear equations

![](https://miro.medium.com/max/445/1*aGJTgo8hfOe_EJSiPxogvA.png)

**homogeneous system of linear equation**

# **Solving the system of linear equation**

The system of linear equation can be solved by converting the augmented matrix formed into row echelon or row reduced echelon form and substitution.

## Types of Solutions

There are three types of solutions which are possible when solving a system of linear equations

## Independent

-   Consistent
-   Unique Solution
-   A row-reduced matrix has the same number of non-zero rows as variables
-   The left hand side is usually the identity matrix, but not necessarily
-   There must be at least as many equations as variables to get an independent solution.

![](https://miro.medium.com/max/271/1*WhCT_7r5WuF19nGoMHh7tw.png)

**When you convert the augmented matrix back into equation form, you get x=3, y=1, and z=2.**

## Dependent

-   Consistent
-   infinitely many solutions
-   Write answer in parametric form
-   A row-reduced matrix has more variables than non-zero rows
-   There doesn’t have to be a row of zeros, but there usually is.
-   This could also happen when there are less equations than variables.

![](https://miro.medium.com/max/269/1*aH-A8EEQiNspcR5d9Rj20A.png)

The first equation will be x + 3z = 4. Solving for x gives x = 4–3z.

The second equation will be y — 2z = 3. Solving for y gives y = 3 + 2z.

The z column is not cleared out (all zeros except for one number) so the other variables will be defined in terms of z. Therefore, z will be the parameter t and the solution is … x = 4–3t, y = 3 + 2t, z = t.since t can be any parameter,so infinite solutions or simply there are less equations than variables so infinite values possible for any one variable.

## Inconsistent

-   No Solution
-   A row-reduced matrix has a row of zeros on the left side, but the right hand side isn’t zero.

![](https://miro.medium.com/max/266/1*_EB3gj_Uqek_z0U7SkccoQ.png)

**There is no solution here. You can write that as the null set Ø, the empty set {}, or no solution.**

It indicates that one the equation is inparticipant to give solution,so,inconsistent.

![](https://miro.medium.com/max/875/1*76tNRIH3KMTQk3hGrViUZA.png)

# Inverse of matrix

The inverse of a matrix A is a matrix that, when multiplied by A results in the identity. The notation for this inverse matrix is A^–1.

The matrix which have their inverse are called invertible matrices and others are called singular,i.e matrix where AA^-1 = I exist are invertible matrices.

The inverse of the matrix can be found using following steps:-

1.  write the augmented matrix consisting of original matrix and Identity matrix with original on left and identity on left.
2.  perform gaussian elimination such that original matrix on left is converted to identity.
3.  During the operation,converted matrix obtained on right side from identity matrix is the reverse of original matrix.

![](https://miro.medium.com/max/621/1*W5jdWvz-pkBCn8BFrNvzeQ.jpeg)
finding inverse of invertible matrix

**(The ‘ symbol will be used to show T which stands for transpose)**

# Projection of vector

Mathematically,projection of vector a on vector b means the part of vector a projected in direction of vector b.This is very intuitive and easy to visualize.

![](https://miro.medium.com/max/254/0*mxC2hwWgiswOfA2D.png)

Projection of a on b or proj(a,b) can be calculated as:- a.b/(|a||b|)

![](https://miro.medium.com/max/685/0*F-cTZPenlvva5q1k.png)

# Projection Matrix

A projection matrix is a matrix which transforms vector from one dimension to other.

Well this is very overlook definition,to understand it in depth,we need to know to about basis,orthogonal projection and stuffs which are easy and required very much in linear algebra but not understanding it will not make much difference in course of Machine Learning here or anywhere.

Taking an example :-

![](https://miro.medium.com/max/88/0*axS4BQv6MrOcE8wj.gif)

This matrix P transforms any vector into y=x.[multiply matrix P with vector [x y]’ ,

Geometrically to the projection of any matrix A in matrix B can be given as A.Proj(B) where Proj(B) gives projection matrix for B.

So Not going much in depth in this topic,projection matrix for any matrix A can be written as :- _P_=_A_(_A’A_)^−1_A’._

For more indepth discussion,you can ping me on linkedin or whatsapp,I will cover the topic in video lecture.

# Eigen Vectors and Eigen Values

Eigen vector of a matrix A is a vector represented by a vector X such that when X is multiplied with matrix A, then the direction of the resultant matrix remains same as vector X..

It means that matrix obtained by product of matrix A and vector X,i.e matrix AX is just a scaled form of vector X.So,AX can be represented as some λX.

AX = λX, and this λ is called as eigen value for that eigen vector. i.e matrix AX is in same direction as X with it’s value/magnitude scaled by λ or it’s eigen values.

Lets understand it more simply,The matrix A is multiplied by a vector X to produce a new transform vector AX.(dim(A) = mxn,dim(X) = nx1,so dim(AX=mx1,hence AX a vector)

When a matrix is multiplied by a vector,there are two possibilities:-

1.  The new transformed vector(product of matrix and vector) is just a scaled form of the original vector.i.e AX = λX.
2.  the transformed vector has no direct scalar relationship with the original vector which we used to multiply to the matrix.

> If the new transformed vector is just a scaled form of the original vector then the original vector is known to be an eigenvector of the original matrix. Vectors that have this characteristic are special vectors and they are known as eigenvectors. Eigenvectors can be used to represent a large dimensional matrix.
> 
> The value by which newly transformed vector is scaled from original vector is called eigen value and large multi-dimensional matrix form of data can be represented by eigen values as features with the importance of feature being eigen value.

We will understand more of data and features and importance of these ahead.

**Finding eigen values and eigen vectors:-**

We use the general definition (AX=λX) to find eigen values and eigen vectors.

A.v = λ.v => (A-λI).v = 0, to calculate eigen values,we do |A-λI| = 0.

so we solve determinant of |A-λI| = 0 to calculate all possible eigen values for that matrix.

The no. of unique λ’s obtained represent the no. of eigen vectors vi’s for that matrix with them being scaled by λi’s.

# Determinant

> Determinant is a very important concept of core linear algebra but we can understand determinant as a function which maps every square matrix with a unique no. used to solve many mathematical equations and matrix systems

## For a 1×1 Matrix

Let A = [a] be the matrix of order 1, then determinant of A is defined to be equal to a.

## For a 2×2 Matrix

For a 2×2 matrix (2 rows and 2 columns):

![](https://miro.medium.com/max/194/0*R8W-XRDxyp_cnVzQ.gif)

determinant of A = ab - cd

## For a 3×3 Matrix

For a 3×3 [matrix](https://www.toppr.com/guides/maths/matrices/matrix/) (3 rows and 3 columns):

![](https://miro.medium.com/max/230/0*JPPFyzmbpnH2a8-8.gif)

The determinant is: |A| = a (ei − fh) − b (di − fg) + c (dh − eg).

![](https://miro.medium.com/max/508/0*lWJ1oxuV8qNnJJla.gif)

## For higher dimension matrices

The pattern continues for higher order matrices with for **4x4** being:-

![](https://miro.medium.com/max/694/0*i8XXLoeAukociiCb.gif)

As a formula:

![](https://miro.medium.com/max/701/0*OnBLIXKVDbTb4363.gif)

Notice the +−+− pattern (+a… −b… +c… −d…).

# Finding Eigen vectors

The eigen values of matrix calculation was discussed as det|A-λI| = 0 giving all possible unique values of λ’s.

After getting eigen value λ,the vector X can be calculated by solving:-

**(A-λI)X = 0**

![](https://miro.medium.com/max/875/1*-23VN2Jzr9-6h4mL-4I-2w.jpeg)

# Principal Component Analysis

By definition:-

> Principal Component Analysis, or PCA, is a dimensionality-reduction method that is often used to reduce the dimensionality of large data sets, by transforming a large set of variables into a smaller one that still contains most of the information in the large set.

Well this definition may not be for our purpose currently,so for followers of my lecture:-

**PCA can be understood as a method of finding most important principal component vectors of matrix or feature vector of large data represented as matrix(both are same things).**

Lets break it,finding most important feature of matrix……….,how to do that?

![](https://miro.medium.com/max/294/1*Y2ONn-1Ht-zfyy_w_zEbYQ.jpeg)

Well it’s simple,find all the eigen vectors and eigen values of **square matrix obtained**,and the eigen vectors are the feature or **principal components** with their importance value reflected by respective eigen values.so,most important vector is eigen vector with highest eigen value and so on…

But

![](https://miro.medium.com/max/324/1*70S6Wb0kHi01wxGs3yTWtA.jpeg)
how the hell will I get **square matrix** every time?

Obviously,you will not get square matrix each time,so as standard method,All matrix are first multiplied with their transpose to form square matrix and then all methods are applied to get principal component vectors.

So let’s analyze steps for PCA :-

1.  Let’s have a data of m products having n feature(n dimension) in form of matrix A of dim mxn,so A’(transpose of A) is matrix of dim nxm.
2.  we multiply A and A’ to get a matrix S = A’A,dim of S is nxn(nxm x mxn = nxn)
3.  This S is called covariance matrix,we do **eigendecomposition** of S.
4.  Eigen decomposistion is a very simple step,for this nxn matrix,there exist n eigen values and n eigen vectors(each having length n i.e equal to length of column vector).
5.  we sort all eigen vectors as per there eigen values in decreasing order and make a set of them i.e matrix of dim nxn( n eigen vector each having length n).
6.  Now,suppose if we want to reduce the dim of data from n to k,so we take only k eigen vectors forming nxk matrix.
7.  To reduce the feature dim,we multiply A(dim mxn) with this newly formed nxk matrix,giving a new matrix of dim mxk(mxn x nxk).
8.  Now,we have matrix having m products with there top k features which is < n.
9.  Remember we sorted eigen vectors as per there eigen values,that is greater the eigen value,more important the feature,so top k eigen vector(having top k eigen values) -> top k feature vector to form.
10.  Step 3 to 5 is called **eigendecomposition** and is important concept in PCA,we will also see it’s use in SVD next.

This is how we have PCA for dimensional reduction in real life machine learning/data science.We learn and apply this ahead in part of this course.

# Singular value Decomposition

![](https://miro.medium.com/max/354/1*FuZijK6_zMdWyrPp9k7ZYw.jpeg)

We decomposed a square matrix in terms of it’s eigen values in PCA.This decomposition of square matrix in form of it’s eigen vectors is called eigendecomposition.

The problem with eigendecomposition is that it can be done only for square matrices,so for factorization or decomposition of non symmetric or non-square matrices,we do singular value decomposition.

It is very important and applicable concept having huge use in machine learning,recommendation system,data computation etc.. .

Let’s understand it in mathematical manner:-

It is the decomposition of a rectangular matrix into product of two orthogonal square and a rectangular diagonal matrix.

![](https://miro.medium.com/max/421/1*9fXtcHdNJSqIP76BBHuwGg.png)

here U and V are orthogonal matrix which means:- U’U = I and V’V = I.

So let’s understand how it is done:-

![](https://miro.medium.com/max/875/1*K1bBSxMmd1657qwasQpIeg@2x.jpeg)

Taking matrix A as

![](https://miro.medium.com/max/104/0*EmLa_w3dI1wXthF2.gif)

1.  Taking a square matrix AA’ (dim = mxm),it’s eigen decomposition is done,i.e all n eigen values are taken and represented as nxn matrix(n eigen vectors each of length n as matrix dim is nxn),this matrix will be called U.

![](https://miro.medium.com/max/446/0*U7pcCZmi8RJyldbE.gif)

![](https://miro.medium.com/max/369/0*bs27zUssciMfFc1Q.gif)

![](https://miro.medium.com/max/211/0*-n0iygvclwvfODeb.gif)

2. Again same step will be done with square matrix A’A(dim nxn),to again eigen decompose it to a matrix of dim nxn called as V.

![](https://miro.medium.com/max/226/0*HZr5X2MGbVwx_Yze.gif)

![](https://miro.medium.com/max/151/0*J9Fd9rT0HEBmWl2v.gif)

3. The middlemost matrix is a diagonal matrix of same dimension as of A with diagonal components being square root of eigen values of AA’ or A’A(both will have same eigen values).

![](https://miro.medium.com/max/136/0*VQBta4c6l8wPeNV6.gif)

The SVD is used for many purpose in real life like sentiment analysis,entity recognition.

![](https://miro.medium.com/max/875/0*_97Oj5y6XwxUO8dp.png)
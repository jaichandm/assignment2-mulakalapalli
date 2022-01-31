# assignment2-mulakalapalli
Created this repo for Web Apps Assignment 2

# Jaichand Mulakalapalli
###### Hyvee located at 1217 South Main St Maryville MO 64468.
Hyvee is a **great place** to buy food. It has a **free huge Parking space**. Opposite to Hyvee there are At&t store & Taco Bell. McDonald's, Scooter's Coffee and Walmart are nearby to Hyvee.

---

###### Directions to Hy-Vee Grocery Store from nearest Airport
Kansas City International Airport(MCI)

1. After coming out of Airport Head west
2. Use the left lane to continue toward NW 120th St
3. Turn left onto L P Cookingham Dr
4. Turn left onto NW 120th St
5. Turn left onto the I-29 N ramp to I-435 W/St Joseph/Topeka
6. Merge with I-29 N
7. Keep left to stay on I-29 N
8. Keep left to stay on I-29 N
9. Take exit 56A for US-71 toward US-59 N/Maryville
10. Continue onto US-71 N
11. Turn left onto US-71 BUS N
12. Turn right
13. Arrive at location: Hy-Vee Grocery Store

My recommendation for others to choose food items at Hyvee

* Go to the Hyvee Store
* Buy Food
     * Rice
     * Tender licious Chicken
     * Lays
     * Fruits
* Come Home

Link to the [AboutMe.md](https://github.com/mjaichand/assignment2-mulakalapalli/blob/main/AboutMe.md).

---

###### Sports Activity
Below Table gives an overview for participants to choose a particular Sport/Activity based on their interest. The Name column represents the name of the sport/activity. The Location column shows the location where to participate in the sport/activity. The Equipment Fee column shows the amount of money for personal equipment.

| Name | Location | Equipment Fee |
| :--- | :--- | :---: |
| Football | next to Colden Hall | 20$ |
| Criket | near Union Ball Room | 30$ |
| TableTennis | opp. Horizon West | 5$ |
| Basketball | Fitness Centre | 10$ |

---

###### Pithy Quotes

> Take long walks in stormy weather or through deep snows in the fields and woods, if you would keep your spirits up. Deal with brute nature. Be cold and hungry and weary.
>> -*Henry David Thoreau*

> Life is like a dogsled team. If you ain't the lead dog, the scenery never changes.
>> -*Lewis Grizzard*

---

###### Code Fencing

>**Dynamic Programming** is mainly an optimization over plain recursion. Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming. The idea is to simply store the results of subproblems, so that we do not have to re-compute them when needed later. This simple optimization reduces time complexities from exponential to polynomial. For example, if we write simple recursive solution for Fibonacci Numbers, we get exponential time complexity and if we optimize it by storing solutions of subproblems, time complexity reduces to linear.
>
>> Source <https://www.geeksforgeeks.org/dynamic-programming/>

You are given a matrix with n rows and m columns. Find the largest submatrix consisting of only zeros (a submatrix is a rectangular area of the matrix).

```
int zero_matrix(vector<vector<int>> a) {
    int n = a.size();
    int m = a[0].size();

    int ans = 0;
    vector<int> d(m, -1), d1(m), d2(m);
    stack<int> st;
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            if (a[i][j] == 1)
                d[j] = i;
        }

        for (int j = 0; j < m; ++j) {
            while (!st.empty() && d[st.top()] <= d[j])
                st.pop();
            d1[j] = st.empty() ? -1 : st.top();
            st.push(j);
        }
        while (!st.empty())
            st.pop();

        for (int j = m - 1; j >= 0; --j) {
            while (!st.empty() && d[st.top()] <= d[j])
                st.pop();
            d2[j] = st.empty() ? m : st.top();
            st.push(j);
        }
        while (!st.empty())
            st.pop();

        for (int j = 0; j < m; ++j)
            ans = max(ans, (i - d[j]) * (d2[j] - d1[j] - 1));
    }
    return ans;
}
```

Code Source <https://cp-algorithms.com/dynamic_programming/zero_matrix.html#implementation>

>**Linear algebra** is a branch of mathematics, but the truth of it is that linear algebra is the mathematics of data. Matrices and vectors are the language of data.
>Linear algebra is about linear combinations. That is, using arithmetic on columns of numbers called vectors and arrays of numbers called matrices, to create new columns and arrays of numbers. Linear algebra is the study of lines and planes, vector spaces and mappings that are required for linear transforms.
>
>> Source <https://machinelearningmastery.com/gentle-introduction-linear-algebra/>

Finding the rank of a matrix

```
const double EPS = 1E-9;

int compute_rank(vector<vector<double>> A) {
    int n = A.size();
    int m = A[0].size();

    int rank = 0;
    vector<bool> row_selected(n, false);
    for (int i = 0; i < m; ++i) {
        int j;
        for (j = 0; j < n; ++j) {
            if (!row_selected[j] && abs(A[j][i]) > EPS)
                break;
        }

        if (j != n) {
            ++rank;
            row_selected[j] = true;
            for (int p = i + 1; p < m; ++p)
                A[j][p] /= A[j][i];
            for (int k = 0; k < n; ++k) {
                if (k != j && abs(A[k][i]) > EPS) {
                    for (int p = i + 1; p < m; ++p)
                        A[k][p] -= A[j][p] * A[k][i];
                }
            }
        }
    }
    return rank;
}

```

Code Source <https://cp-algorithms.com/linear_algebra/rank-matrix.html>

>**Numerical methods** is basically a branch of mathematics in which problems are solved with the help of computer and we get solution in numerical form.
>In other words those methods are numerical methods in which mathematical problems are formulated and solved with arithmetic operations and these arithmetic operations are carried out with the help of high level programming language like C, C++, Python, Matlab etc on computer.
>
>>Source <https://www.codesansar.com/numerical-methods/>

Ternary Search

```
double ternary_search(double l, double r) {
    double eps = 1e-9;              //set the error limit here
    while (r - l > eps) {
        double m1 = l + (r - l) / 3;
        double m2 = r - (r - l) / 3;
        double f1 = f(m1);      //evaluates the function at m1
        double f2 = f(m2);      //evaluates the function at m2
        if (f1 < f2)
            l = m1;
        else
            r = m2;
    }
    return f(l);                    //return the maximum of f(x) in [l, r]
}
```

Code Source <https://cp-algorithms.com/num_methods/ternary_search.html>
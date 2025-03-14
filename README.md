# POLICY EVALUATION

## AIM
To develop a Python program to evaluate the given policy.

## PROBLEM STATEMENT
To find best policy from two policies which are defined by user using policy evaluation function.

## POLICY EVALUATION FUNCTION
```
def policy_evaluation(pi, P, gamma=1.0, theta=1e-10):
    prev_V = np.zeros(len(P), dtype=np.float64)
    # Write your code here to evaluate the given policy
    while True:
      V=np.zeros(len(P))
      for s in range(len(P)):
        for prob,next_state,reward,done in P[s][pi(s)]:
           V[s]+=prob*(reward+gamma *prev_V[next_state]*(not done))
      if np.max(np.abs(prev_V-V))<theta:
        break
      prev_V=V.copy()
    return V
```
## POLICY 1
```
 pi_frozenlake = lambda s: {
    0: RIGHT,
    1: DOWN,
    2: RIGHT,
    3: LEFT,
    4: DOWN,
    5: LEFT,
    6: RIGHT,
    7:LEFT,
    8: UP,
    9: DOWN,
    10:LEFT,
    11:DOWN,
    12:RIGHT,
    13:RIGHT,
    14:DOWN,
    15:LEFT #Stop
}[s]
print_policy(pi_frozenlake, P, action_symbols=('<', 'v', '>', '^'), n_cols=4)

```
## POLICY 2
```
pi_2 = lambda s: {
    0: DOWN,
    1: RIGHT,
    2: RIGHT,
    3: DOWN,
    4: LEFT,
    5: RIGHT,
    6: DOWN,
    7: LEFT,
    8: DOWN,
    9: RIGHT,
    10: LEFT,
    11: DOWN,
    12: RIGHT,
    13: DOWN,
    14: RIGHT,
    15: LEFT  # Stop at goal
}[s]

print("Name: NARESH.R")
print("Register Number: 212223240104")
print_policy(pi_2, P, action_symbols=('<', 'v', '>', '^'), n_cols=4)
```
## STATE VALUE FUNCTION
```
V1 = policy_evaluation(pi_frozenlake, P,gamma=0.99)
print_state_value_function(V1, P, n_cols=4, prec=5)

V2 = policy_evaluation(pi_2, P, gamma=0.99)

print("\nState-value function for Your Policy:")
print_state_value_function(V2, P, n_cols=4, prec=5)
```
## BEST POLICY
```
if np.sum(V1 >= V2) == len(V1):
    print("\nThe first policy is the better policy.")
elif np.sum(V2 >= V1) == len(V2):
    print("\nYour policy is the better policy.")
else:
    print("\nBoth policies have their merits.")
V1>=V2

if(np.sum(V1>=V2)==11):
  print("The first policy is the better policy")
elif(np.sum(V2>=V1)==11):
  print("The second policy is the better policy")
else:
  print("Both policies have their merits.")
```

## OUTPUT:
![Screenshot 2025-03-14 145001](https://github.com/user-attachments/assets/acf6874c-81ec-4cf1-b701-fbddf66e4b1f)


![image](https://github.com/user-attachments/assets/0858b9f3-8b49-441b-833f-3940be5b570f)


## RESULT:
Thus, The Python program to evaluate the given policy is successfully executed.


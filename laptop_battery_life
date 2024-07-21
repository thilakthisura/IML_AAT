import sys
data = float(sys.stdin.readline())
training_data = {} 
data_num = 100 


def clean_input(string):
    new_pts= string.split(",")
    return [float(x) for x in new_pts]

with open("trainingdata.txt","r") as training:
    for i in range(0,data_num):
        instance = clean_input(training.readline())
        training_data[instance[0]] = instance[1]

max_life = max(training_data.values()) 
max_case = [] 
lin_case = {} 

for key in training_data:
    if training_data[key] < max_life:
        lin_case[key] = training_data[key]
    else:
        max_case.append(key)

full_battery = min(max_case)

def sum_xys(dict):
    total = 0
    for x in dict:
        total += (x * dict[x])
    return float(total)

def sum_xs(dict):
    total = 0
    for x in dict:
        total += x
    return float(total)

def sum_ys(dict):
    total = 0
    for x in dict:
        total += dict[x]
    return float(total)

def sum_x_sqrd(dict):
    total = 0
    for x in dict:
        total += x**2
    return float(total)

def lin_regr(dict):
    n = len(dict)
    xys = sum_xys(dict)
    xs = sum_xs(dict)
    ys = sum_ys(dict)
    x_sqrd = sum_x_sqrd(dict)
    
    m = ((n * xys) - (xs * ys)) / ((n * x_sqrd) - (xs**2))
    b = ((x_sqrd * ys) - (xs * xys)) / ((n * x_sqrd) - (xs**2))
    
    return [m,b]

lin_vars = lin_regr(lin_case)

def est_life(chrg_time):
    if chrg_time >= full_battery:
        batt_life = max_life
    else:
        m = lin_vars[0]
        b = lin_vars[1]
        batt_life = (m * chrg_time) + b
    return batt_life

print(est_life(data))
    

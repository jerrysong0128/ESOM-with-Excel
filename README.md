# Model Description
Corresponding Author: Jerry Song; jerrysong0128@gmail.com

This simplified Energy System Optimization model utilizes Excel Solver. It is tailored to the circumstances in Brazil and is designed to enhance their electricity supply system with various energy sources. The data utilized in this model is sourced from the CCG project.

For citation: https://doi.org/10.21203/rs.3.rs-893535/v1

## **Objective Function:**

$$ min\sum_y\frac{Total\ Cost(y)}{{(1+r)}^y} $$

***r*** denotes the discount rate; ***y*** denotes the year; The objective function is to minimize the total discounted cost for each year.

$$ Total Cost(y) = Investment Cost(y) + O\&M cost(y) + Fuel Cost(y) $$

- **Investment Cost**

$$ Investment Cost= \sum_t Cap^{new}_{t}×Cost^{inv}_{t} $$

<b><i>Cap<sup>new</sup></i></b> denotes the new capacity built in year y;<b><i>Cost<sup>inv</sup></i></b> denotes the investment cost per unit capacity;The investment cost is sum of investment for new capacity among all technologies.

- **O&M Cost**

$$ O\&M cost= \sum_t Capt^{opr}_{t}×Cost_{t}^{O\&M} $$

<b><i>Cap<sup>opr</sup></i></b> denotes the operating capacity in year y; <b><i>Cost<sup>O&M</sup></i></b> denotes the O&M cost per unit capacity; The investment cost is sum of O&M cost for operating capacity among all technologies.

$$ Cap_{t}^{opr} (y)= Cap_{t}^{new}(y)+Cap_{t}^{opr}(y-1)-Cap_{t}^{ret}(y) $$
  
<b><i>Cap<sup>opr</sup></i></b> denotes the operating capacity in year y; <b><i>Cap<sup>new</sup></i></b> denotes the new capacity built in year y;  <b><i>Cap<sup>ret</sup></i></b> denotes the retired capacity in year y; The operating capacity in year y is the sum of operating capacity in year y-1 and new built capacity this year and minus the retired capacity this year.

- **Fuel Cost**

$$ Fuel Cost_{t} =Cap_{t}^{opr}×Cost_{t}^{fuel} $$

<b><i>Cap<sup>opr</sup></i></b> denotes the operating capacity in year y; <b><i>Cost<sup>fuel</sup></i></b> denotes the fuel cost per unit capacity; The investment cost is sum of fuel cost for operating capacity among all technologies that use fuel.</b>
## **Constrains:**
- **Demand Constrains**

$$ Demand≤ \sum_t Cap_{t}^{opr}×Efy_{t}×CF_{t} $$

<b><i>Cap<sup>opr</sup></i></b> denotes the operating capacity in year y; <b><i>Efy<sub>t</sub></i></b> denotes the efficiency of a given technology; <b><i>CF<sub>t</sub></i></b> denotes the Capacity Factor of a given technology, which means their availability throughout a year; The maximum possible supply is the product of the operating capacity, the efficiency, and the capacity factor. The total energy supply is the sum of maximum possible supply from all operating capacity among technologies. And it should be larger than the energy demand set exogenous.

- **Emission Constrains**

$$ Emission Limit≥ \sum_t Cap_{t}^{opr}×EF_{t} $$

<b><i>Cap<sup>opr</sup></i></b> denotes the operating capacity in year y; <b><i>EF<sub>t</sub></i></b> denotes the emission intensity per unit capacity; The total emission is the sum of emission from operating capacity among all technologies. And it should be lower than the emission limit set exogenous.

- **Capacity Growth Constrains**

$$ Capt^{opr}(y=0)×(1+CGCt)y≥ Capt^{opr}(y) $$

<b><i>Cap<sup>opr</sup>(y=0)</i></b> denotes the operating capacity in the beginning year ; <b><i>CGC<sub>t</sub></i></b> denotes the capacity growth constrains factor for a given technology; The capacity growth constrains is the product of initial operating capacity and the growth rate with power of a given year. The the growth rate, which is <b><i>CGC<sub>t</sub></i></b>, should be set exogenously. And the capacity growth constrains should be larger than the operating capacity in year y.
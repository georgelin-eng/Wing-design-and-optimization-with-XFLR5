For information on structural design of wings: [Aerotoolbox. Wing structural design](https://aerotoolbox.com/wing-structural-design/](https://aerotoolbox.com/wing-structural-design/)

For information on optimizing aircraft wings: [Design Informatics Lab. Optimization of an Aircraft Wing
](https://designinformaticslab.github.io/_teaching//designopt/projects/2016/desopt_2016_08.pdf)


> [! Wing Design Process] 
> 1. Low reynolds and high lift airfoils (see [http://airfoiltools.com](http://airfoiltools.com/search/index "http://airfoiltools.com/search/index") and UIUC Airfoil Data Site)
> 2. 2D analysis in XFLR5
> 3. Airfoils shortlist
> 4. 3D wing testing with a select few combinations in XFLR5
> 5. Selection of best airfoil combinations for wing and tail
> 6. Adjusting wing parameters to meet specifications   



---

# Airfoils

### Getting a shortlist of airfoils to test

Go to [http://airfoiltools.com](http://airfoiltools.com) and the [UIUC Airfoil Database](https://m-selig.ae.illinois.edu/ads/coord_database.html) and look for airfoils. From my experience on wings last year, these were the two main functions for airfoils that we’re selecting for.

- **Lift generating - for use on wings**
    - Decently cambered
    - Good Cl/Cd performance
    - Soft stall
    - High lift
    - Thick
    - Easy to manufacture
- **Symmetrical - for use on tail*
    - Low drag
    - Easy to manufacture

### Airfoil terminology
![[Pasted image 20230807210958.png]]

|Parameter|Effects|General Guidelines|
|---|---|---|
|Camber|- Lift generation<br>    <br>- Soft stall|- Symmetrical - no camber<br>    <br>- Lift generating - 4 to 10%|
|Thickness|- Larger airfoils are easier to work with when it comes to construction|- Symmetrical -<br>    <br>- Lift generating - over 15%|
|Chord|- Smaller chord lengths increase aspect ratio (good thing)<br>    <br>- Smaller chord has reduced drag and leads to weight savings<br>    <br>- Lower lift so bigger wing is needed|- The restriction on chord length is based mostly on the storage case we’ll be using|
||||
|Angle of Attack (AOA)|- Higher AOA increases lift<br>    <br>- Higher AOA increases drag<br>    <br>- Too high of an AOA leads to stall|- Find AOA that has high lift (Cl) and near peak Cl/Cd|
|Center of Pressure (CoP)|- Effects aircraft stability|- must be behind Cg or else we’ll crash|


---



# Wings

![[Pasted image 20230807211008.png]]

|Parameter|Effects|General Guidelines|
|---|---|---|
|Wing span|- Having a larger wing leads to:<br>    <br>    - higher lift generation<br>        <br>    - less maneuverability<br>        <br>    - increased bending loads|- Fit it into the case<br>    <br>- Large enough to meet lift requirements<br>    <br>- High enough AR for low drag|
|Chord|- Smaller chord lengths increase aspect ratio (good thing)<br>    <br>- Smaller chord has reduced drag and leads to weight savings<br>    <br>- Lower lift so bigger wing is needed|- Large enough to meet lift requirements<br>    <br>- Otherwise, don’t make it too large since it’s less efficient|
|Twist (variation in AOA along span)|- Effects stall characteristics<br>    <br>- Helps with stability|- Have lower AOA at tips so that the root stalls first|
|Sweep|- Leads to lower AR, therefore increasing drag<br>    <br>- Moves lift distribution towards wing tips<br>    <br>- Increases Cl but decreases Cl/Cd|- Not recommended since we’re not going to be going supersonic: [source](https://aerotoolbox.com/intro-sweep-angle/)<br>    <br>- This parameter is controlled by offset in XFLR5|
||||
|Taper Ratio|Tip chord / Root chord<br><br>- Moves lift generation towards root<br>    <br>- Reduces wing area|- Calculated as: Tip chord / Root chord<br>    <br>- Adjust to optimize elliptical curve<br>    <br>- Lowest induced drag is seen at taper ratios of round 0.4: [source](https://dergipark.org.tr/tr/download/article-file/629766)|
|Aspect Ratio (AR)|- Increasing aspect ratio makes the plane more stable but less maneuverable<br>    <br>- Reduces induced drag|- Find optimal aspect ratio that leads to a greater Cl/Cd (6 to 8)|


# Analyzing Lift Polars


| Common Polars                                | Graph examples                                                                                                                                                                                              | Optimal Characteristics                                                             |     
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | 
| Cl vs AOA                                    | ![[Pasted image 20230807211258.png]]                                                                                                                                                                        | Aim for something that has soft stall (smoothly decreases after peak) and a good Cl |     |
| Cl/Cd vs AOA (lift-to-drag coeff.)           | **![](https://lh4.googleusercontent.com/bCyiAMT6agy6Rihcx1RlT57Tn1WVyE51feWd55L6bcbEJuf0XvlkckTI92FhwPhwEFQSkblHLfppUYwJ0aAczO4Fa0zLCxWhxauucxpGVPEtAS1sqZ2tghV1T_3b1zNhGT27o8jLhkH0r6XYWQKaWquVmg=s2048)** | Aim for a curve that has a broad range of optimal lift-drag coeff.                  |     |
| Cm vs AOA                                    | ![[Pasted image 20230807213440.png]]                                                                                                                                                                        | Aim for something near zero or negative for expected AOAs. The graph should also have a gentle slope.                           |     |
| Elliptical curve (optimal lift distribution) | ![[Pasted image 20230807212431.png]]                                                                                                                                                                        | Adjust taper ratio and wing twist to get a more optimal lift curve                  |     |




# Other Relevant Analysis

![[Pasted image 20230807212158.png]]

Hinge moments will also need to be calculated for ailerons so that servos have the necessary torque. This analysis is done in XFOIL.

# Simulation of Observable Effects of Cluster Member Speed Reduction

## Introduction

### Purpose

This code simulates an open star cluster and surrounding field stars to model and visualize the observable effects (from Earth) of reducing the speed of cluster member stars.

### Relevance

Understanding the dynamics of star clusters and how internal velocity changes manifest in observable parameters (like proper motion, radial velocity) is crucial in astrophysics. Gaia observations provide precise astrometric and kinematic data, making such simulations essential for interpreting real-world observations.

### Presumptions

* The simulation simplifies the complex gravitational interactions within a star cluster.
* Initial conditions (spatial and velocity distributions) significantly influence the outcome.
* The observer (Earth) is far enough from the cluster to apply certain geometric approximations.

## Code Description

### Star Generation

#### Cluster Stars

##### Spatial Distribution

The code uses a Plummer model to generate the initial spatial distribution of cluster stars. This model is chosen to represent a typical density profile of star clusters, with a higher density of stars towards the center.

##### Velocity Distribution

Cluster stars are assigned velocities drawn from a Gaussian distribution. The mean and dispersion of this distribution are parameters that can be adjusted.

##### Justification

The Plummer model provides a reasonable approximation of the spatial structure of many observed open clusters. The Gaussian velocity distribution is a common assumption in the absence of more specific knowledge about the cluster's dynamical history.

#### Field Stars

##### Spatial Distribution

Field stars are generated randomly within a defined cubic volume. This represents the general background population of stars in the galaxy.

##### Velocity Distribution

Field stars are also assigned velocities from a Gaussian distribution, but with different parameters (mean and dispersion) than the cluster stars, to reflect the distinct kinematic properties of the field population.

##### Justification

Random spatial distribution is a simplified representation of the field star distribution. The Gaussian velocity distribution is, again, a common statistical model.

### Speed Modification

The code includes functionality to modify the velocities of cluster members.

#### Constant Speed Addition

Adds a constant velocity vector pointing radially outwards from the cluster center to each cluster member.

#### Gaussian Speed Addition

Adds a velocity component whose magnitude follows a Gaussian distribution with respect to the distance from the cluster center (stars closer to the center have a larger additional speed).

#### Justification

These modifications allow for exploration of how different velocity profiles within a cluster affect its observed properties. For example, the Gaussian speed addition could mimic the effect of dynamical processes that preferentially accelerate stars near the cluster's core.

### Coordinate Transformation

The code transforms the simulated spatial and velocity data into observable coordinates (Right Ascension, Declination, parallax, proper motion, radial velocity) as seen from Earth.

This transformation takes into account:

* The distance and location of the cluster center relative to Earth.
* The motion of the cluster center relative to Earth.

##### Justification

This is essential to connect the simulated intrinsic properties of the cluster to what astronomers actually measure.

### Observable Calculations

* Parallax: Calculated from the distance of each star.
* Proper Motion: Calculated from the transverse velocities of the stars.
* Radial Velocity: Calculated from the component of the star's velocity along the line of sight.

##### Justification

These are the fundamental observables used to study the kinematics of star clusters.

### Visualization

The code generates plots to visualize:

* Spatial distribution of stars.
* Velocity distribution.
* Proper motion vectors.
* Distribution of stars in observable coordinates (RA, Dec, parallax, radial velocity).

##### Justification

Visualization is crucial for understanding the complex 3D data and for identifying patterns in the simulated observables.

## Presumptions and Limitations

* **Simplified Dynamics:** The simulation does *not* include the gravitational interactions between stars. Stars are generated with initial positions and velocities, and their subsequent motion is not calculated. This is a major simplification, as gravity is the dominant force in star clusters.
* **Initial Conditions:** The results of the simulation are highly dependent on the initial spatial and velocity distributions. Different choices for the Plummer radius, velocity dispersion, etc., will lead to different observable properties.
* **Observer Distance:** The code assumes that the observer (Earth) is located at a large distance from the cluster. This allows for the use of certain approximations in the coordinate transformations.
* **Coordinate System Alignment:** The simulation assumes a direct alignment between the simulation's Cartesian coordinates and the observer's coordinate system. In reality, a rotation would be needed.
* **Constant Velocity Modification:** The constant and Gaussian speed additions are artificial manipulations. They are not intended to represent realistic physical processes but rather to explore the *sensitivity* of observable parameters to velocity changes.

## Procedure to Run the Code

* The code is written in Python and requires libraries like NumPy, Pandas, and Matplotlib.
* The user can modify various parameters, such as:
    * Number of cluster and field stars.
    * Cluster size and density profile.
    * Cluster and field star velocity distributions.
    * Cluster distance and motion.
    * Parameters for the speed modification functions.
* The code outputs:
    * A Pandas DataFrame containing the simulated stars and their properties (both in simulation coordinates and observable coordinates).
    * Various plots visualizing the spatial and velocity distributions of the stars.

## Expected Results and Interpretation

By comparing the observable properties of the simulated cluster *with* and *without* the speed modifications, the user can investigate:

* How changes in the internal velocities of cluster members affect the cluster's appearance on the sky (RA, Dec distribution).
* How velocity changes influence the proper motion of cluster members.
* Whether velocity changes have a significant impact on the parallax and radial velocity distributions.

The plots of proper motion vectors are particularly important, as they can reveal the overall motion of the cluster and any internal kinematic structure.

The simulation can help to understand the challenges in interpreting real observational data and the importance of considering various factors that can affect the observed properties of star clusters.

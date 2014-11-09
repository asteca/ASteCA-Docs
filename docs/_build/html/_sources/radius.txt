Cluster radius estimation
=========================

We begin
by counting the number of RDP points that fall below a given maximum tolerance
interval above $d_{field}$. When the number of these points reaches a
fixed value, $n_{fixed}$, the point closest to $d_{field}$ is stored as the
most probable radius for this iteration. This process is repeated increasing
the tolerance around $d_{field}$ which results in another probable radius
being stored, not necessarily the same found in the previous iteration. The
final estimation for $r_{cl}$ and its associated error comes from averaging
the set of radius values stored this way and taking its standard deviation,
respectively.

By manually
adjusting the value for $n_{fixed}$ in the input data file (set by default
as $20\%$ of the total number of points in the RDP) the user can relax or
restrict the algorithm if needed.
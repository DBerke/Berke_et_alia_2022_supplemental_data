Introduction
------------------------------
This repository contains supplemental data files for the papers Berke et al. 2022a,b (hereafter B22a * B22b) and Murphy et al. 2022 on constraining variation in the fine-structure constant (_alpha_) using solar twins. Some of the information is duplicated between files, in order to better associate it with different variables.

Directory structure
------------------------------

`17_pair_separation_files/`
=========================

   These files contain the (weighted mean) separations between each of the 17 pairs of transitions for which Q-coefficients are available for both transitions in the 130 solar analogs considered in B22b. The files contain a header row at the beginning of the file, with the format as follows. All columns extect the first two are in units of m/s.

* `star_name`: the name of the star
* `Nobs`: the number of observations
* `model_offset_pair`: the difference between the measured pair separation in the star and the expected pair separation from the model derived in B22b.
* `err_stat_pair`: the statistical error in the separation measurement.
* `err_sys_pair`: the systematic error determined to remain in the measurment, as estimated in B22b using the chi-squared-per-degree-of-freedom for the distribution. This value can be zero (i.e, the statistical error is sufficient to explain the variation seen in the distribution), though in practice this only happens for some pairs (and transitions) after the HARPS fiber change.
* `chisq_nu_pair`: the chi-squared-per-degree-of-freedom measured for the pair after subtracting the expected model value.
* The remaining 8 columns have the same 4 values for the 2 transitions involved in the pair:
	* `offset_transition<1|2>`: the difference between the measured wavelength of the transision and the expected wavelength of the transition in the star, based on the model for each transition derived in B22b.
	* `t_stat_err<1|2>`: the statistical error in the wavelength of the transition.
	* `t_sys_err<1|2>`: the systematic error determined to remain in the measurement of the transition wavelength, as estimated in B22b.
	* `chisq_nu<1|2>`: the chi-squared-per-degree-of-freedom for the transition wavelength distribution.
   
   
`data/`
=========================
`Stellar_sample_all.csv` contains information on the 164 stars which were selected for this analysis using the initial "solar-type stars" parameters in B22b. The columns are as follows:

* `name`: designation of the star.
* `T_eff`: effective temperature (K).
* `[Fe/H]`: metallicity.
* `logg`: logarithm (base-10) of the surface gravity of the star in cm/s^2.
* `absMag`: absolute magnitude (Johnson-Cousins system).
* `(b-y)`: (b–y) color (Strömgren system).
* `NObsPre`: number of observations prior to the HARPS optical fiber change in May 2015.
* `NObsPost`: number of observations after the HARPS fiber change.
* `NObsTotal`: total number of observations.

Based on modelling done in B22b (Sec. 3.5.1 & Fig. 6), stars with T_eff > 6072 K or [Fe/H] < –0.45 were not used, though we retain them in this file for completeness.

`pair_moodel_coefficients/`
=========================
The two files contained in this directory hold the coefficients determined for each pair of transitions as detailed in B22b, where the coefficients are to be used in Eq. 4. The format is as follows:

* `Transition 1`, `Transition 2`: the transitions in the pair. Wavelength is in Ångstroms, with the element and ionization included.
* `Order`: The echelle order the pair was measured in (since some pairs can be measured independently on two adjacent orders). The numbering is simply ordinal, running from 0-71 to cover the 72 effective orders present in HARPS.
* `sigsys`: the systematic error determined to remain in the measurement of this pair (as discussed above). Units are m/s.
* `a, b_1, c_1, d_1, b_2, c_2, d_2`: the remaining columns hold the coefficients for Eq. 4 in B22b, with the names corresponding to their use in the equation. Units are m/s, as is the output of the equation.


`pair_separations_and_errors/`
=========================
This directory holds files with the pair separation and errors (on the mean and on the weighted mean) for all pairs in the 130 stars considered in B22b. In each file the first column is the star identifier, followed by columns for each pair, which are identified by the header at the top. The files with "17" in the name contain the results only for the 17 pairs for which _q_-coefficients are available (the sample in B22a), while the equivalently-named files without a number contain results for all the pairs considered in B22b (of which the sammple of B22a is a subset).

* `pair_separations_<pre|post>.csv`>: contain the pair separations.
* `pair_eotm_<pre|post>.csv`: contain the **e**rror **o**n **t**he **m**ean.
* `pair_eotwm_<pre|post>.csv`: contain the **e**rror **o**n **t**he **w**eighted **m**ean.

Both types of errors are included because in determining the systematic error the error used for each star is the larger of the two.
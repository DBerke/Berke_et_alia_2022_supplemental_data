Introduction
------------------------------
This repository contains supplemental data files for the papers Berke et al. 2022a ("Probing Galactic variations in the fine-structure constant using solar twin stars: methodology and results") and Berke et al. 2022b  ("Probing Galactic variations in the fine-structure constant using solar twin stars: systematic errors"; hereafter B22a & B22b), both in the Monthly Notices of the Royal Astronomical Society. Some of the information is duplicated between files, in order to better associate it with different variables.

Contents
------------------------------

`17_pair_separation_files/`
=========================

   These files contain the (weighted mean) separations between each of the 17 pairs of transitions for which _q_-coefficients are available for both transitions in the 130 solar analogs considered in B22b. The files contain a header row at the beginning of the file, with the format as follows. The first two columns have no units; the rest are in m/s.

* `star_name`: the identifier for the star (the name "Vesta" refers to observations of the Sun taken by reflection off the asteroid Vesta).
* `Nobs`: the number of observations of each star.
* `model_offset_pair`: the difference between the measured pair separation in the star and the expected pair separation from the model derived in B22b.
* `err_stat_pair`: the statistical error in the separation measurement.
* `err_sys_pair`: the systematic error determined to remain in the measurment, as estimated in B22b using the chi-squared-per-degree-of-freedom for the distribution. This value can be zero (i.e, the statistical error is sufficient to explain the variation seen in the distribution), though in practice this only happens for some pairs after the HARPS optical fiber change in 2015.
* `chisq_nu_pair`: the chi-squared-per-degree-of-freedom measured for the pair after subtracting the expected model value.
* The remaining 8 columns have the same 4 values for the 2 transitions involved in the pair:
	* `offset_transition<1|2>`: the difference between the measured wavelength of the transition and the expected wavelength of the transition in the star, based on the model for each transition derived in B22b.
	* `t_stat_err<1|2>`: the statistical error in the wavelength of the transition.
	* `t_sys_err<1|2>`: the systematic error determined to remain in the measurement of the transition wavelength, as estimated in B22b the same way as for pairs of transitions.
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

`NIST_formatted_transitions_with_blends.txt` contains information on the transitions used in B22a & b. The columans are as follows:

* `lambda(nm,vac)`: The wavelength of the transition, in vacuum, in nm.
* `wavenumber`: The wavenumber of the transition, in 1/cm.
* `species`: The atomic or ionic species of the transition.
* `lower energy - upper energy` The energies of the lower and upper orbital states of the transition, in 1/cm.
* `lower orbital configuration`: The quantum mechanical configuration of the lower orbital state.
* `lower J`: the angular momentum of the lower orbital state.
* `upper orbital configuration`: the quantum mechanical configuration of the upper orbital state.
* `upper J` the angular momentum of the upper orbital state.
* `normalized depth`: the normalized depth of the absorption feature corresponding to this transition in a HARPS observation of the Sun reflected off Vesta (0 is the continuum, 1 would be fully saturated).
* `blendedness`: the degree of blending observed in the absorption feature corresponding to this transition in a HARPS observation of the Sun. Runs from 0 to 5, where 0 means "no detectable blending" and 5 means "extremely blended". The scale was established by visual inspection of the data and is ultimately arbitrary, but reasonably corresponds to increased scatter in transitions with higher blendedness. Generally, 3 or below should be "safe" to use.

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

`transition_separations_and_errors/`
==========================
This directory holds files with the transition separation and error, similar to the pair separations described above. The only differences are that the columns have labels referring to transitions rather than pairs, and the files with "22" in the name contain the results for the 22 transitions for which _q_-coefficients are available in Appendix 1 of B22a.
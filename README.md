# LS_Series_Gaps_Jupyter

This routine analyses the effect of data gaps on the spectral output of the Lomb-Scargle (LS) algorithm applied to a sythetic harmonic time-series.
The gaps may be padded with zeros or simple jumps from the end of one data sequence to the beginning of the next.
The gaps may also be cut-off abruptly (using an inverse top-hat window function) or tapered through the used of a Tukey filter.

The dataset is simple: 1000 points with a 0.01 day cadence, resulting in a 10-day time-series. It comprises of a superposition of four in-phase sinusoidal signals with frequencies of 1, 2, 3 and 4 cycles per day, respectively, all with unit amplitudes.

A number of time-series are created with data gaps between 0% to 99% of the full data range (i.e. 0 to 990 points in steps of 10 points), all centralized with respect to the time-series. Among other options, characteristics of the time-series may be controlled using a number of switches:
- abrupt onset of the gap using an inverse top-hat function, or taper to zero with a Tukey filter. For the latter, the taper length is adjustable,
- retain zeros within the gap to pad the dataset, or remove to produce a data-jump. Both options have different effects on the characteristics of the LS signals,
- the normalization of LS amplitudes to better relate certain results,
- add noise to the time-series,
- save the plots to file.



# LS_Series_Gaps_Jupyter

This routine analyses the effect of data gaps on the spectral output of the Lomb-Scargle (LS) algorithm applied to a sythetic harmonic time-series.
The gaps may be padded with zeros or simple jumps from the end of one data sequence to the beginning of the next.
The gaps may also be cut-off abruptly (using an inverse top-hat window function) or tapered through the used of a Tukey filter.

The dataset is simple: 1000 points with a 0.01 day cadence, resulting in a 10-day time-series. It comprises of a superposition of four in-phase sinusoidal signals with frequencies of 1, 2, 3 and 4 cycles per day, respectively, all with unit amplitudes.
A number of time-series are created with data gaps between 0% to 99% of the full data range (i.e. 0 to 990 points in steps of 10 points), all centralized with respect to the time-series.
Through the use of a switch, these gaps may be abrupt through the use of an inverse top-hat function, or tapered to zero with a Tukey filter. For the latter, the taper length is adjustable.
Another switch dictates whether the zeros within the gap are retained to pad the dataset, or removed, causing a time gap. Both types of gap have different effects on the amplitudes within the LS periodogram.
The LS amplitudes may be normalized via the use of another switch to better relate the results of the unpadded dataset.
Two more switches exist to add noise to the time-series and to save the plots to file.

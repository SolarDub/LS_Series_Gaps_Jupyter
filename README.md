# LS_Series_Gaps_Jupyter

This routine analyses the effect of data gaps on the spectral output of the Lomb-Scargle (LS) algorithm applied to a sythetic harmonic time-series.
The gaps may be padded with zeros or simple jumps from the end of one data sequence to the beginning of the next.
The gaps may also be cut-off abruptly (using an inverse top-hat window function) or tapered through the used of a Tukey filter.

The dataset is simple: 1000 points with a 0.01 day cadence, resulting in a 10-day time-series. It comprises of a superposition of four in-phase sinusoidal signals with frequencies of 10, 20, 30 and 40 cycles per day, respectively, all with unit amplitudes.

----

![50pcTimeSeries](https://user-images.githubusercontent.com/81772405/201449555-810eea74-2ee6-44e9-b7a1-f0d51a7fbdc9.jpg)

**Figure 1:** Synthetic 10-day time-series at 0.01-day candence (*blue*). Modulating this signal with an inverse top-hat window function (*green dashes*) creates an abrupt gap within the center of the time-series. The entry and exit points of the gap may be tapered to and from zero by modulating the signal with a new window-function (red), where the inverse top-hat is tapered with a Tukey filter of a user-defined size (101 elements in this case).

----

A number of time-series are created with data gaps between 0% to 99% of the full data range (i.e. 0 to 990 points in steps of 10 points), all centralized with respect to the time-series. Among other options, characteristics of the time-series may be controlled using a number of switches:
- abrupt onset of the gap using an inverse top-hat function, or taper to zero with a Tukey filter. For the latter, the taper length is adjustable,
- retain zeros within the gap to pad the dataset, or remove to produce a data-jump. Both options have different effects on the characteristics of the LS signals,
- the normalization of LS amplitudes to better relate certain results,
- add noise to the time-series,
- save the plots to file.

With zero gap, the Lomb-Scargle spectrum displays all four signals with unit amplitude at their respective frequencies. Note that no artifacts exist around the signal peaks, the shapes of which are simple artifacts of the 0.1 cycle per day frequency resolution.

----

<img src="https://user-images.githubusercontent.com/81772405/201450431-fd3dfa3e-6816-4735-8c62-a61f5aaba260.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201450434-43ca9895-dece-4455-be6a-0607b214f215.jpg" width="400" />

**Figure 2:** Lomb-Scargle frequency spectrum of a time-series with no gap and no noise. (*Left*) The full spectrum showing the four components of the time series. (*Right*) The 10 cycles per day unit-amplitude peak shows no artifacts. It drops immediately to zero at 0.1 cycles per day either side of the peak, relating to the frequency resolution of the spectrum.

----

While various combinations of switches maybe applied to the analysis with the output being produced for any data-gap, in what follows, for the purposes of an example, Lomb-Scargle amplitudes will be produced from a noiseless time-series with a data-gap of 50% (see Figure 1) that is:
(a) unpadded, abruptly cut-off gap (inverse top-hat),
(b) padded, abruptly cut-off gap (inverse top-hat),
(c) unpadded, tapered gap (Tukey, 51 elements for each taper),
(d) padded, tapered gap (Tukey, 51 elements for each taper).

For simplification the LS amplitudes around the first peak of 10 cycles per day (Figure 2, *left*) will be displayed. Figure 3 illustrates these examples in four plots.

----

<img src="https://user-images.githubusercontent.com/81772405/201485322-32cb6bb4-54f4-4695-9442-487f61794dd6.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201485336-8417517a-3c95-47d0-b129-784ef04ab864.jpg" width="390" />
<img src="https://user-images.githubusercontent.com/81772405/201485363-6dda6974-2bff-4952-8227-496569bb60a1.jpg" width="390" /><img src="https://user-images.githubusercontent.com/81772405/201485371-026b14d7-e42f-4c70-83d0-880c5b15dda8.jpg" width="390" />

**Figure 3:** Plots of the 10 cycles per day peak for a time-series with a centralized gap extent of 50% of the time-range for the examples (a)-(d) as described in the text.

----

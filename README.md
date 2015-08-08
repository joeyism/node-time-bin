# time-bin
A module that takes in time series and outputs the binned version of it. This was a fork of [timestamp-binning](https://github.com/belici/timestamp-binning).

## Installation
To install, simply run

    > npm install --save time-bin

## Usage

    var timestampBinner = require('time-bin');
         
    //create a new timestamp binner:
    var evalPeriod = "week";
    var binSize = "day";
    var binner = new timestampBinner(evalPeriod, binSize);
    
    //some dummy timestamps (dates) as examples:
    var d1 = new Date(2014, 5, 27, 21, 20, 0, 0);
    var d2 = new Date(2014, 5, 29, 2, 20, 0, 0);
    var d3 = new Date(2014, 5, 28, 23, 20, 0, 0);
    
    //add an array of time stamps:
    binner.addTimestamps([d1, d3, d3, d3, d2]);
    
    console.log(binner.hist);
    //will output: [ 0, 0, 0, 0, 1, 3, 1 ]
    
    //add a single timestamp
    binner.addTimestamp(d1);
    
    console.log(binner.hist);
    //will output: [ 0, 0, 0, 0, 2, 3, 1 ]

## Differences from timestamp-binning
* time-bin bins in the past times, instead of future
* time-bin exclude time that is outside of the range

## Version
**1.0.0**
* First publish

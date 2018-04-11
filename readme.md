# Signal Database

Storing labeled time series data to a database. Please see example.

MIT license
This isn't intended for public use as it isn't documented well. However, if you get it
then you are free to use it however you want.

## NOTES



### LabeledData

    SignalBundle signal_bundle -> lists of lists emulating an nd array
    list labels -> a label string for every sample

    plotbins()
        plots the signals in the signal bundle with different colors corresponding
        to the different label names

    label_data(indices, labels)
        assigns the label text to the corresponding indices

### SignalBundle

    name -> name of signal
    signals -> lists of lists (can do lists of numpy 1d array)
    timestamps -> timestamps because signals are usually time domain things


### SignalDB
    I use the pydblite database library.
    *NOTE:* Signals that already exist in the database cannot be added again.
    The signals are hashed. This helps retrieve signals using just the data rather than an identifier.
    The first signal in the signal bundle of the corresponding labeled data is used to create the hash.

    SignalDB(name) -> constructor, name is the name of the database.
        It will be called this when it create the database file. If the file exists
        in the local directory, then it will use that database. Don't provide the extension

    add_labeleddatq() -> adds a SignalBundle

    commit() -> commits the database. This means it will update the file stored on the disc
        or create a new file if it doesn't exist.

    sdb.get_labeleddata() -> retrieves all the labelled data as a list.

    findld() -> provide labeled data to retrieve the corresponding labeled data in the database. This is useful when
        you want to update the same signalbundles' labels multiple times using the signal data. Trust me, when you work with
        this stuff you'll understand why I added this feature.

### SelectData
    This is used to open up a matplotlib plot and select a block of data to
        label it

    SelectData(timestamps, signals)

    sd.boxSelect() -> run this to pull up the plot of the data. With the mouse
        click and drag to make a selection. After this nothing happens. Just close the window.












> `gbox-betatom` is a gbox that implements betato. It is part of the standard gbox set.



### Prerequisites

You mainly need a working copy of [Docker](http://docker.com). It is used
exclusively to manage system configurations for running numerous tools
across numerous platforms.

### Installation

* All docker images are at "https://hub.docker.com/u/granatumx".
* All github repos are at "https://github.com/granatumx/*".

First set up your scripts and aliases to make things easier. This command should pull the container if
it does not exist locally which facilitates installing on a server.

```
source <( docker run --rm -it granatumx/scripts:1.0.0 gx.sh )
```

This command makes `gx` available. You can simply run `gx` to obtain a list of scripts available.

The GranatumX database should be running to install gboxes. The gbox sources do not need to be installed.
A gbox has a gbox.tgz compressed tar file in the root directory which the installer copies out and uses
to deposit the preferences on the database. Since these gboxes are in fact docker images, they will be
pulled if they do not exist locally on the system. Convenience scripts are provided for installing specific gboxes.


```
$ gx run.sh                                       # Will start the database, taskrunner, and webapp
$ gx installGbox.sh granatumx/gbox-betatom:1.0.0  # Install this gbox

# Now go to http://localhost:34567 and see this gbox installed when you add a step.
```

### Notes

Many methylation datasets use the Beta-value (ranging from 0 to 1) to measure the percentage of methylation. This
gbox converts these values into the log2 ratio of the intensities of methylated probe versus unmethylated probe (m-value).

    The "epsilon" parameter is for avoiding infinite results. The full formula for this conversion is:

        y = log((x + epsilon) / (1 - x + epsilon))


# SSH tunneling (specific example for anvi'o)
Very brief and simple tutorial on how to SHH tunnel in order to view figures in anvio for example.

### Step 1: Open terminal (and do not access HPC)

### Step 2: Begin SSH tunneling

Type 
```ssh -L 8090:localhost:8090 skoog@eofe7.mit.edu```

or for you WHOI folks it will look more like:

```ssh -L 8930:localhost:8930 eskoog@poseidon-l2.whoi.edu```

I believe you can write either `l1` or `l2`. 

Once you press enter it should look like you are on your HPC. In my case, it will show `skoog@eofe7` instead of `base`.

![](https://i.imgur.com/A6eSjTr.png)



### Step 2: Activate your anvi'o environment 
```conda activate anvio-7.1```

### Step 3: Navigate to working directory 

Go to directory where you want to perform function (like visualize anvio figure). Example:

```cd work/MAGs/```

### Step 4: Run your anvi-interactive command 

 MAKE SURE YOU ADD  ```--server-only -P 8090``` flags

```anvi-interactive --manual-mode \
anvi-interactive --manual-mode \
                 -d GENOMES-completeness-MATRIX.txt \
                 -t GENOMES-completeness-MATRIX.txt.newick \
                 -p GENOMES_metabolism_PROFILE.db \
                 --title "Shark Bay MAG Metabolism Heatmap" \
                 --server-only -P 8090
```
### Step 5: Access figure from web browser

Go to your web browser and type:

```
http://localhost:8090
```

Hit the DRAW button at the bottom left and your figure should pop up! Happy editing!

![](https://i.imgur.com/uW1gsMg.jpg)





## 

## Extra (Jupyter Notebooks)

Looking to use SHH tunneling for work in jupyter notebooks?

### Simple steps:

1. Open HPC and type 

    `jupyter notebook --no-browser --port=8939` 

2. Open terminal for local computer and write
`ssh -N -f -L localhost:8939:localhost:8939 eskoog@poseidon-l2.whoi.edu` 
(with whatever port number you were given)

3. Then go to web browser and type 

    `localhost:8939`

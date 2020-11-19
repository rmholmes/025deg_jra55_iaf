# 025deg_jra55_iaf
Standard configuration for 0.25 degree [ACCESS-OM2](https://github.com/COSIMA/access-om2) experiment (ACCESS-OM2-025) with JRA55-do interannual forcing (IAF).

For usage instructions, see the [ACCESS-OM2 wiki](https://github.com/COSIMA/access-om2/wiki).

Run length and timestep are set in `accessom2.nml`. The default timestep for this configuration is 1350 seconds, and the model is stable with this timestep right from the start. After the first year or two of model equilibration you may be able to run with a 1800s timestep for faster throughput.

**NOTE:** All ACCESS-OM2 model components and configurations are undergoing continual improvement. We strongly recommend that you "watch" this repo (see button at top of screen; ask to be notified of all conversations) and also watch [ACCESS-OM2](https://github.com/COSIMA/access-om2), all the [component models](https://github.com/COSIMA/access-om2/tree/master/src), and [payu](https://github.com/payu-org/payu) to be kept informed of updates, problems and bug fixes as they arise.

# RMH: Notes on how to start a new cycle:

git clone --no-hardlinks 025deg_jra55_iaf_cycle1 025deg_jra55_iaf_cycle2
cd 025deg_jra55_iaf_cycle2
git checkout -b omip_cycle2
mkdir /scratch/e14/rmh561/access-om2/archive/025deg_jra55_iaf_cycle2
ln -s /scratch/e14/rmh561/access-om2/archive/025deg_jra55_iaf_cycle2 archive
cp -r /scratch/e14/rmh561/access-om2/archive/025deg_jra55_iaf_cycle1/restart060 archive/restart060
ln -s /scratch/e14/rmh561/access-om2/archive/025deg_jra55_iaf_cycle1/output060 archive/output060

- edited `archive/restart060/accessom2_restart.nml` to have
        ```
         FORCING_CUR_DATE        = 1958-01-01T00:00:00,
          EXP_CUR_DATE    = 1958-01-01T00:00:00
          ```
          - edited `archive/restart060/ocean/ocean_solo.res` to have
          ```
          1958     1     1     0     0     0        Model start time:
          year, month, day, hour, minute, second
          1958     1     1     0     0     0        Current model
          time: year, month, day, hour, minute, second
          ```
          - set `use_restart_time = .false.` in `ice/cice_in.nml`

- Run a single year.
- set use_restart_time = .true. in ice/cice_in.nml
- Keep running...

# RMH: Notes on errors:

cycle 3:

Ice thermo, 1959.


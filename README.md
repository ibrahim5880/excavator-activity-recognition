# Excavator Activity Recognition — Multi-Sensor IMU Dataset

Motion data recorded from an excavator during post-earthquake demolition operations
following the 6 February 2023 Kahramanmaraş earthquakes (Türkiye). This dataset supports
the article:

> Karatas, I., & Budak, A. *Deep Learning-Based Classification of Excavator Activities from
> Multi-Sensor Motion Data in Post-Earthquake Demolition Operations.* Canadian Journal of
> Civil Engineering (accepted).

## Data collection

| Item | Value |
|---|---|
| Sensor | MbientLab MetaMotion IMU (device `E6498D061C1A`), mounted on the excavator arm |
| Channels | 3-axis accelerometer, 3-axis gyroscope, 3-axis magnetometer |
| Sampling rate | 50 Hz |
| Sessions | 2 (14 November 2023; 08:19 and 13:56 local time, UTC+03:00) |
| Activities | `demolition`, `grading`, `loading`, `waiting` |
| Labelling | Activity intervals assigned from synchronized field video recordings |

## Repository structure

```
data/
├── raw/        # Original MetaMotion exports, one file per sensor and session
│   ├── MetaMotion1_2023-11-14T08.19.28.683_E6498D061C1A_Accelerometer.csv   (session 1)
│   ├── MetaMotion1_2023-11-14T08.19.28.683_E6498D061C1A_Gyroscope.csv
│   ├── MetaMotion1_2023-11-14T08.19.28.683_E6498D061C1A_Magnetometer.csv
│   ├── MetaMotion1_2023-11-14T13.56.38.460_E6498D061C1A_Accelerometer.csv   (session 2)
│   ├── MetaMotion1_2023-11-14T13.56.38.460_E6498D061C1A_Gyroscope.csv
│   └── MetaMotion1_2023-11-14T13.56.38.460_E6498D061C1A_Magnetometer.csv
└── labeled/    # Sensors merged on the accelerometer timeline, with activity labels
    ├── session1_labeled.csv
    └── session2_labeled.csv
```

### Raw files (`data/raw/`)

| Column | Description |
|---|---|
| `epoc (ms)` | Unix epoch time in milliseconds |
| `timestamp (+0300)` | Local time (UTC+03:00) |
| `elapsed (s)` | Seconds since start of the session |
| `x-axis`, `y-axis`, `z-axis` | Accelerometer in g, gyroscope in deg/s, magnetometer in T |

### Labeled files (`data/labeled/`)

| Column | Description |
|---|---|
| `activity` | Activity label: `demolition`, `grading`, `loading`, `waiting` |
| `epoc` | Unix epoch time in milliseconds |
| `timestamp` | Local time (UTC+03:00) |
| `elapsed` | Seconds since start of the session |
| `acc_x_axis`, `acc_y_axis`, `acc_z_axis` | Acceleration (g) |
| `gyr_x_axis`, `gyr_y_axis`, `gyr_z_axis` | Angular velocity (deg/s) |
| `mag_x_axis`, `mag_y_axis`, `mag_z_axis` | Magnetic field (T) |

### Class distribution (labeled files, 50 Hz samples)

| Activity | Session 1 | Session 2 | Total samples | ≈ Duration (min) |
|---|---:|---:|---:|---:|
| demolition | 208,431 | 14,498 | 222,929 | 74.3 |
| waiting | 107,247 | 98,421 | 205,668 | 68.6 |
| grading | 5,654 | 126,047 | 131,701 | 43.9 |
| loading | 0 | 43,044 | 43,044 | 14.3 |
| **Total** | **321,332** | **282,010** | **603,342** | **201.1** |

## Citation

If you use this dataset, please cite the article above and this dataset (see the DOI badge /
Zenodo record for the dataset citation).

## License

The dataset is released under the [Creative Commons Attribution 4.0 International
(CC BY 4.0)](LICENSE) license.

## Contact

Ibrahim Karatas — Osmaniye Korkut Ata University, Department of Civil Engineering
(ibrahimkaratas@osmaniye.edu.tr, ORCID [0000-0003-0845-4536](https://orcid.org/0000-0003-0845-4536))

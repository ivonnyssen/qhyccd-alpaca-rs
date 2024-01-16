# qhyccd-alpaca

[![Crates.io](https://img.shields.io/crates/v/qhyccd-alpaca.svg)](https://crates.io/crates/qhyccd-alpaca)
[![Codecov](https://codecov.io/github/ivonnyssen/qhyccd-alpaca/coverage.svg?branch=main)](https://codecov.io/gh/ivonnyssen/qhyccd-alpaca)
[![Dependency status](https://deps.rs/repo/github/ivonnyssen/qhyccd-alpaca/status.svg)](https://deps.rs/repo/github/ivonnyssen/qhyccd-alpaca)

ASCOM Alpaca driver for QHYCCD cameras and filter wheels written in Rust.

## Current state

### Tested Operating Systems

- Debian 12 (Bookworm) amd64
- Ubunutu 22.04.3 LTS arm64 (Raspberry Pi 4)
- Raspberry Pi OS arm64 (Raspberry Pi 4)

### Tested Cameras

| Camera Model | ASCOM Validation Status |
| ------------ | ------ |
| QHY5III290C  | Passed |
| QHY5III178M  | Failed - exposure fails with error code 0x2001 |
| QHY178M      | Passed |
| QHY600M      | Passed |

### Tested Filter Wheels

| Filter Wheel Model | ASCOM Validation Status |
| ----------- | ------ |
| QHYCFW3L-SR | Passed |

### Tested Software

- SharpCap
- ACP
- NINA
- SGP

## Installation

### Prerequisites

The driver relies on the QHYCCD SDK version 23.09.06 and libusb-1.0.0.
The instructions below are for installing from source.

#### Debian / Ubuntu / Raspberry Pi OS

##### Install libusb-1.0.0 and build tools

```bash
sudo apt-get install -y build-essential libusb-1.0-0-dev
```

##### Install QHYCCD SDK

```bash
wget https://www.qhyccd.com/file/repository/publish/SDK/230906/sdk_Arm64_23.09.06.tgz
tar xzvf sdk_Arm64_23.09.06.tgz 
cd sdk_Arm64_23.09.06/
sudo sh install.sh
```

### Install via Rust / Cargo

Install Rust and Cargo using [rustup](https://rustup.rs/).

```bash
cargo install qhyccd-alpaca
```

### Or build from source

#### Clone the repository

```bash
git clone https://github.com/ivonnyssen/qhyccd-alpaca.git
cd qhyccd-alpaca
cargo build --release
```

### Run the driver

```bash
cd target/release
./qhyccd-alpaca [--help for more info]
```

## Rust version requirements

qhyccd-alpaca works with stable Rust. The minimum required Rust version is 1.75.0.

## Missing features

- LiveMode is not implemented
- The driver only supports cameras that can transfer 16bit images
(almost all cameras can though)
- FastReadout is implemented using the Control::Speed property in the driver, however
this control is not available on any of my cameras, so it is untested.
- Pulse guiding is not implemented
- If you find anything else missing or wrong, please open an [issue](https://github.com/ivonnyssen/qhyccd-alpaca/issues/new).

## License

This project is licensed under either of

- Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or
   <https://www.apache.org/licenses/LICENSE-2.0>)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or
   <https://opensource.org/licenses/MIT>)

at your option.

### Contribution

All contributions are welcome.

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in qhyccd-alpaca by you, as defined in the Apache-2.0 license,
shall be dual licensed as above, without any additional terms or conditions.

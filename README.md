# Athenz Setup on AWS

- [Build the Project](#build-the-project)
- [ZMS Setup](#zms-setup)
- [ZTS Setup](#zts-setup)
- [UI Setup](#ui-setup)

## Build the Project

First make sure to checkout Athenz source and this aws-setup
repositories in one of your directories.

```
git clone https://github.com/AthenZ/athenz-aws-cf-setup.git
git clone https://github.com/AthenZ/athenz.git
```

Next, we're going to build the Athenz zms, zts and ui
binary packages:

```
cd athenz
mvn clean install
```

Once the build is successfully completed, copy the generated
tar files to their respective directories in the aws setup
repo directory:

```
mkdir ../athenz-aws-cf-setup/ui-setup/tars
cp ./assembly/ui/target/athenz-ui-<version>-bin.tar.gz ../athenz-aws-cf-setup/ui-setup/tars/athenz-ui-bin.tar.gz

mkdir ../athenz-aws-cf-setup/zms-setup/tars
cp ./assembly/zms/target/athenz-zms-<version>-bin.tar.gz ../athenz-aws-cf-setup/zms-setup/tars/athenz-zms-bin.tar.gz

mkdir ../athenz-aws-cf-setup/zts-setup/tars
cp ./assembly/zts/target/athenz-zts-<version>-bin.tar.gz ../athenz-aws-cf-setup/zts-setup/tars/athenz-zts-bin.tar.gz
```

Now we need to build the aws setup Athenz configuration utility
and copy to our build directories for packer setup:

```
cd ../athenz-aws-cf-setup/athenz-conf-aws
make
cp target/linux/athenz-conf-aws ../ui-setup/build/bin/
cp target/linux/athenz-conf-aws ../zts-setup/build/bin/
```

Now follow the sections below to deploy ZMS, ZTS and UI
components in AWS.

## ZMS Setup

Refer [AWS ZMS Setup](docs/aws_zms_setup.md) for details

## ZTS Setup

Refer [AWS ZTS Setup](docs/aws_zts_setup.md) for details

## UI Setup

Refer [AWS UI Setup](docs/aws_ui_setup.md) for details

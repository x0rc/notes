# Installing Docker on Kali Linux

`docker-ce` can be installed from Docker repository. One thing to bear in mind, [Kali Linux is based on Debian](https://www.kali.org/docs/policy/kali-linux-relationship-with-debian/), so we need to use [Debian’s current stable version](https://www.debian.org/releases/stable/) (even though Kali Linux is a [rolling distribution](https://www.kali.org/docs/general-use/kali-branches/)). At the time of writing (Dec. 2021), its “bullseye”:

```bash
printf '%s\n' "deb https://download.docker.com/linux/debian bullseye stable" |
  sudo tee /etc/apt/sources.list.d/docker-ce.list
```

```console
curl -fsSL https://download.docker.com/linux/debian/gpg |
  sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/docker-ce-archive-keyring.gpg
```

```console
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```
# hashs

allows to calculate several hash functions simultaneously 


## installation

make the bash `hashs` script executable and move it to one of your `$PATH` folders :

```shell
$ chmod +x ./hashs

$ echo $PATH
/home/user/.local/bin:/bin:/usr/bin:/usr/local/bin

$ # for personal use
$ mv ./hashs /home/user/.local/bin

$ # for system use
$ sudo mv ./hashs /usr/local/bin/
```

`hashs` uses [xxHash](https://github.com/Cyan4973/xxHash) non-cryptographic hash function : you can install it if you want to use it or delete the corresponding line of te script if you don't want to use it.


## usage

`hashs` can process one or more files :

```shell
$ hashs /tmp/zfs.disk 
/tmp/zfs.disk
size   : 3276800
M date : 2019-03-19 09:29:52
A date : 2019-03-19 10:13:21
C date : 2019-03-19 09:29:52
xxh64  : fa22b5e113963903
md5    : 708d4dc6e7096d01adaa0e79ca9d727b
sha1   : 8fcad952fea87e0f99557cccad919ceb00dcc5e8
sha256 : d8e039fa55e7d087d31dfccf2c227dec0537ab753841d50121c78145fc89525d

$ hashs /tmp/z*.disk
/tmp/zfs.disk
size   : 3276800
M date : 2019-03-19 09:29:52
A date : 2019-03-19 10:15:47
C date : 2019-03-19 09:29:52
xxh64  : fa22b5e113963903
md5    : 708d4dc6e7096d01adaa0e79ca9d727b
sha1   : 8fcad952fea87e0f99557cccad919ceb00dcc5e8
sha256 : d8e039fa55e7d087d31dfccf2c227dec0537ab753841d50121c78145fc89525d

/tmp/zol.disk
size   : 3276800
M date : 2019-03-19 10:17:01
A date : 2019-03-19 10:17:01
C date : 2019-03-19 10:17:01
xxh64  : 267e255eac404a83
md5    : 4aee71421bcecd550191cf3ecdf0fc33
sha1   : fda88b21a38bef77266f4ee027d5989078105ce2
sha256 : bbcaade415a47515be4a1742b53bfd7b66174f0384022d8f398e52e9c82773c1
```

and read from standard input :

```shell
$ hashs < /tmp/zfs.disk 
/dev/stdin
xxh64  : fa22b5e113963903
md5    : 708d4dc6e7096d01adaa0e79ca9d727b
sha1   : 8fcad952fea87e0f99557cccad919ceb00dcc5e8
sha256 : d8e039fa55e7d087d31dfccf2c227dec0537ab753841d50121c78145fc89525d

$ cat splited.* | hashs
/dev/stdin
xxh64  : fa22b5e113963903
md5    : 708d4dc6e7096d01adaa0e79ca9d727b
sha1   : 8fcad952fea87e0f99557cccad919ceb00dcc5e8
sha256 : d8e039fa55e7d087d31dfccf2c227dec0537ab753841d50121c78145fc89525d
```
```shell
# pv /dev/sda1 | hashs
499MiO 0:00:03 [ 124MiB/s] [================================>] 100%            
/dev/stdin
xxh64  : a511b74c40a55a76
md5    : 3ff5cae5ad36ac8e9371f9836b403587
sha1   : e06accc824ed2073c71a2f7a55155dca189d5910
sha256 : a76ccc02aa4cc836abc07a606835817fb28b8a535655fca12ab226571db29fb2
```

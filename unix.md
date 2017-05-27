# Unix Commands

* Create a symbolic link aka symlink aka soft link:
```
ln -s path_to_file_name link_name
```

 * rsync to a remote directory
```
rsync -a file_to_send username@remote_host:destination_dir
```

* bash alias
```
alias command="echo 'command now says this'"
```

* find tricks
> http://vstark.net/2013/06/12/linux-find-tricks/

* copy multiple directories to another directory  
```
cp -r css images js backups ar/

```
> http://unix.stackexchange.com/questions/68455/better-way-to-copy-multiple-directories-to-new-directory
* set vim no swap
```
:set noswapfile, or without the ":" in your vimrc file
```
> http://stackoverflow.com/questions/821902/disabling-swap-files-creation-in-vim

* unzip bz2

> http://superuser.com/questions/480950/how-to-decompress-a-bz2-file 

> Try the following:

```
bzip2 -d filename.bz2
```
> Note, that this command will not preserve original archive file.

> To preserve the original archive, add the -k option:

```
bzip2 -dk filename.bz2
```

* zip all directories in a directory
```
for i in */; do zip -r "${i%/}.zip" "$i"; done

```
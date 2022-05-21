# download-openbsd
A GitHub Action for downloading OpenBSD compilation files -- you know, in case you want to do something crazy, like...try to compile OpenBSD stuff on Linux.

```yaml
- name: Download OpenBSD compilation stuff
  id: download-openbsd
  uses: mario-campos/download-openbsd@v1
  with:
    arch: amd64
    version: 7.1
- name: Build
  env:
    CPATH: ${{ steps.download-openbsd.outputs.root }}/usr/include
    OPENBSD_ROOT: ${{ steps.download-openbsd.outputs.root }}
  run: bmake -I "$OPENBSD_ROOT/usr/share/mk"
```

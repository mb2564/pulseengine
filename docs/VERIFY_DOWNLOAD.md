# Verify a PulseEngine Beta Download

Each public beta release should contain:

- `pulseengine-beta.tgz`
- a versioned tarball such as `pulseengine-0.3.0-beta.15.tgz`
- `SHA256SUMS.txt`

Verify the package before installing it.

## macOS / Linux

From the directory containing the downloaded files:

```bash
sha256sum -c SHA256SUMS.txt
```

If your macOS installation does not provide `sha256sum`:

```bash
shasum -a 256 pulseengine-beta.tgz
```

Compare the output with the `pulseengine-beta.tgz` line in `SHA256SUMS.txt`.

## Windows PowerShell

```powershell
Get-FileHash .\pulseengine-beta.tgz -Algorithm SHA256
```

Compare the displayed hash with the `pulseengine-beta.tgz` entry in `SHA256SUMS.txt`.

## Then install

From the React + Vite repository you want to test:

```bash
npm install --save-dev ./pulseengine-beta.tgz
npx pulseengine version
npx pulseengine init --project .
```

The version command should report the beta version described by the GitHub Release.

A checksum confirms that the downloaded bytes match the published release asset. It does not replace normal software-review or endpoint-security practices.

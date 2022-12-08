name: Build

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: windows-latest
    steps:
    - uses: actions/checkout@v3
    - name: Checkout and build PowerApps pack/unpack tool
      run:  git clone https://github.com/microsoft/PowerApps-Language-Tooling.git
    - name: Setup .NET
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: 6.0.x
    - name: Build PowerApps pack/unpack tool
      run: .\PowerApps-Language-Tooling\build.cmd
    - name: Prepare output folder
      run: mkdir buildoutput
    - name: Pack Milestones
      run: |
            cd Milestones
            ..\PowerApps-Language-Tooling\bin\Debug\PASopa\PASopa.exe -pack .\DataverseSolution\CanvasApps\msft_milestones_5daaa.msapp .\DataverseSolution\CanvasApps\msft_milestones_5daaa_DocumentUri_src\
            powershell rm DataverseSolution\CanvasApps\msft_milestones_5daaa_DocumentUri_src\
            powershell Compress-Archive DataverseSolution\* DataverseSolution.zip
            powershell Compress-Archive TeamsCustomApp\* TeamsCustomApp.zip
            mkdir Milestones
            move DataverseSolution.zip Milestones
            move TeamsCustomApp.zip Milestones
            powershell Move-Item -Path Milestones -Destination buildoutput
            cd ..
    - name: Pack outputs
      run: powershell Compress-Archive buildoutput\* AppPackages.zip
    - name: Create Release
      id: create_release
      uses: actions/create-release@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tag_name: ${{ github.RUN_NUMBER }}
        draft: false
        prerelease: false
    - name: Upload Release Asset
      uses: actions/upload-release-asset@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        upload_url: ${{ steps.create_release.outputs.upload_url }} # This pulls from the CREATE RELEASE step above, referencing it's ID to get its outputs object, which include a `upload_url`. See this blog post for more info: https://jasonet.co/posts/new-features-of-github-actions/#passing-data-to-future-steps 
        asset_path: AppPackages.zip
        asset_name: AppPackages.zip
        asset_content_type: application/zip

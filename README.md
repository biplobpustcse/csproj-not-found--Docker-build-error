# csproj-not-found--error

#### F:\Practice Project\dotNET8\DotNet8WebAPI\DotNet8WebAPI>docker build -t counter-image -f Dockerfile .

```
[+] Building 1.0s (9/17)                                                                                               docker:default
 => [internal] load .dockerignore                                                                                                0.0s
 => => transferring context: 2B                                                                                                  0.0s
 => [internal] load build definition from Dockerfile                                                                             0.1s
 => => transferring dockerfile: 920B                                                                                             0.0s
 => [internal] load metadata for mcr.microsoft.com/dotnet/sdk:8.0                                                                0.5s
 => [internal] load metadata for mcr.microsoft.com/dotnet/aspnet:8.0                                                             0.2s
 => [build 1/7] FROM mcr.microsoft.com/dotnet/sdk:8.0@sha256:7ef41132b2ebe6166bde36b7ba2f0d302e10307c3e0523a4539643a77233f56d    0.0s
 => [base 1/2] FROM mcr.microsoft.com/dotnet/aspnet:8.0@sha256:3ff67792728179308c4bf06799d8b45d155c60fddc347acf69465a496d9a20b8  0.1s
 => => resolve mcr.microsoft.com/dotnet/aspnet:8.0@sha256:3ff67792728179308c4bf06799d8b45d155c60fddc347acf69465a496d9a20b8       0.1s
 => [internal] load build context                                                                                                0.1s
 => => transferring context: 28.70kB                                                                                             0.0s
 => CACHED [build 2/7] WORKDIR /src                                                                                              0.0s
 => ERROR [build 3/7] COPY [DotNet8WebAPI/DotNet8WebAPI.csproj, DotNet8WebAPI/]                                                  0.0s
------
 > [build 3/7] COPY [DotNet8WebAPI/DotNet8WebAPI.csproj, DotNet8WebAPI/]:
------
Dockerfile:11
--------------------
   9 |     ARG BUILD_CONFIGURATION=Release
  10 |     WORKDIR /src
  11 | >>> COPY ["DotNet8WebAPI/DotNet8WebAPI.csproj", "DotNet8WebAPI/"]
  12 |     RUN dotnet restore "./DotNet8WebAPI/./DotNet8WebAPI.csproj"
  13 |     COPY . .
--------------------
ERROR: failed to solve: failed to compute cache key: failed to calculate checksum of ref 9e37cae4-8140-4353-bb83-2f808342532d::killyix207x5mgk70ml8vgdwq:
"/DotNet8WebAPI/DotNet8WebAPI.csproj": not found
```
#### Instead, go to the parent directory, with the .sln file and use the docker -f option to specify the Dockerfile to use in the subfolder:

```
docker build -t counter-image -f DotNet8WebAPI/Dockerfile .
```
#### It worked for me.

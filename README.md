# docker-for-win-bug
Illustrating a bug in docker-for-window

To reproduce the bug, simply:

1) Clone this repo. Make sure you have shared the drive where the repo lives in the docker settings.
2) In the repo directory, on windows, run `docker-compose run bug bash`
3) Then, inside the docker container, run `cd /app`, then `npm install zeromq`

Expected: The zeromq package is built and installed

Actual: The zeromq package fails to build because, during configure: `configure: error: C compiler cannot create executables`

I have the drive shared in the docker settings. The problem appears to be related to the drive being mounted, becuase if you don't cd into `/app`, but instead stay in `/` before running `npm install zeromq`, the build succeeds.

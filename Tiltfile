docker_compose('docker-compose.yml')


# Records the time from a code change to a new process.
# Normally, you would let Tilt do deploys automatically, but this
# shows you how to set up a custom workflow that measures it.
local_resource(
  'deploy',
  'python3 now.py > start-time.txt')

# Add a live_update rule to our docker_build.
docker_build('example-html-image', '.', live_update=[
  sync('.', '/app'),
  run('./report-deployment-time.sh'),
  run('sed -i "s/Hello cats/Congratulations, you set up live_update/g" index.html'),
])

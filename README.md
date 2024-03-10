# Docker-CLI-password-generator
Docker container that allows to generate random uuid4 passwords.

The amount of passwords generated can be manually adjusted. <br />
Can also be used in pipes. <br />
Python script is generated on the fly using heredoc, so no file management is needed.  <br />
It can generate virtually anything, not only passwords. This format is used as an example. <br />

The command to create a container:
```
docker container create -i --name password-generator python bash -c 'cat <<EOF | python -    
import uuid
print(\"\n\".join(str(uuid.uuid4()) for _ in range(`cat -`)))
EOF
'
```
and then you can run it like:
```
echo <number of passwords> | docker container start -i password-generator
```
If you want to store the result just use:
```
echo <number of passwords> | docker container start -i password-generator > <some-file>
```

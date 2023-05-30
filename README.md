# helium-chirpstack-decoders
Repository collection for helium Chirpstack v4 decoders for lorawan devices.
These decoders should be compatible with all Chirpstack v4 LNS's unless specified.

# todo & project structure
1. Clarify structure for project. Suggest `vendor/device/<device_name>-chirpstack-v4.js` for now.
2. There is a standard ts013 which can be found here [TS013-1.0.0 Payload Codec API](https://resources.lora-alliance.org/home/ts013-1-0-0-payload-codec-api) i will work on creating a template folder for these.
2. Dont steal other people decoders as your own, give credit where credit is due. Edited to work with chirpstack should be ok.
3. Anyone wanting to help let me know and i'll add you.
4. work on being able to git clone project directly into to chirpstack.
5. pr away...
6. there is a standard ts013 which can be found here [TS013-1.0.0 Payload Codec API](https://resources.lora-alliance.org/home/ts013-1-0-0-payload-codec-api)

# to use and deploy mkdocs...
- git clone the project and cd into it..
- python -m venv venv
- pip install -r requirements.txt
- `mkdocs serve` to load site to http://localhost:8000/
- commit changes to branch.
- `mkdocs gh-deploy --strict --force` to create and upload to github pages to https://ccall48.github.io/helium-chirpstack-decoders/

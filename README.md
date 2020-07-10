#!/usr/bin/env python3

import json
from urllib import request
from urllib.error import HTTPError


WEBHOOK_URL = 'https://discord.com/api/webhooks/730922866811338813/X--FvtgJRuEGbU3n4pRLNDfaAetvWRJkqGM8TBejnix4KxevmeJ_fVMGNYr6vb_omBon'

# La payload
payload = {
    'content': "Bienvenue dans l'apocalypse! Viens nous aider à combatre les rôdeurs!"
}

# Les paramètres d'en-tête de la requête
headers = {
    'Content-Type': 'application/json',
    'user-agent': 'Mozilla/5.0 (X11; U; Linux i686) Gecko/20071127 Firefox/2.0.0.11'
}

# Enfin on construit notre requête
req = request.Request(url=WEBHOOK_URL,
                      data=json.dumps(payload).encode('utf-8'),
                      headers=headers,
                      method='POST')

# Puis on l'émet !
try:
    response = request.urlopen(req)
    print(response.status)
    print(response.reason)
    print(response.headers)
except HTTPError as e:
    print('ERROR')
    print(e.reason)
    print(e.hdrs)
    print(e.file.read())

RELEASE_NAME_PREFIX ?= usdfprod
HELM_FOLDER ?= ../../../helm
SECRET_PATH ?= secret/rubin/usdf-panda/
CNPG_VERSION ?= 1.16

server:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/panda -f $(HELM_FOLDER)/panda/values.yaml -f values-server.yaml  > server.yaml

idds:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/idds -f $(HELM_FOLDER)/idds/values.yaml -f values-idds.yaml > idds.yaml

activemq:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/msgsvc -f values-msgsvc.yaml  > activemq.yaml

iam:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/iam -f $(HELM_FOLDER)/iam/values.yaml -f values-iam.yaml > iam.yaml

harvester:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/harvester -f $(HELM_FOLDER)/harvester/values.yaml -f values-harvester.yaml  > harvester.yaml

bigmon:
	helm template $(RELEASE_NAME_PREFIX) $(HELM_FOLDER)/bigmon -f $(HELM_FOLDER)/harvester/values.yaml > bigmon.yaml

helm: activemq iam idds server harvester bigmon

cnpg-operator:
	curl -L https://raw.githubusercontent.com/cloudnative-pg/cloudnative-pg/release-$(CNPG_VERSION)/releases/cnpg-$(CNPG_VERSION).0.yaml > cnpg-operator.yaml
	kubectl apply -f cnpg-operator.yaml

get-secrets-from-vault:
	mkdir -p etc/.secrets/
	set -e; for i in username password; do vault kv get --field=$$i $(SECRET_PATH) > etc/.secrets/$$i ; done

clean-secrets:
	rm -f etc/.secrets/


dump:
	kubectl kustomize . | yh

apply:
	kubectl apply -k .

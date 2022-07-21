RELEASE_NAME_PREFIX ?= usdfprod

HELM_FOLDER ?= ../../../helm

activemq:
	helm template $(RELEASE_NAME_PREFIX)-activemq $(HELM_FOLDER)/msgsvc -f $(HELM_FOLDER)/msgsvc/values.yaml -f $(HELM_FOLDER)/msgsvc/values/values-lsst.yaml -f $(HELM_FOLDER)/msgsvc/values/values-use-secret.yaml > activemq.yaml

iam:
	helm template $(RELEASE_NAME_PREFIX)-iam $(HELM_FOLDER)/iam -f $(HELM_FOLDER)/iam/values.yaml -f $(HELM_FOLDER)/iam/values/values-lsst.yaml -f $(HELM_FOLDER)/iam/values/values-use-secret.yaml > iam.yaml

idds:
	helm template $(RELEASE_NAME_PREFIX)-idds $(HELM_FOLDER)/idds -f $(HELM_FOLDER)/idds/values.yaml -f $(HELM_FOLDER)/idds/values/values-lsst.yaml -f $(HELM_FOLDER)/idds/values/values-use-secret.yaml > idds.yaml

panda:
	helm template $(RELEASE_NAME_PREFIX)-server $(HELM_FOLDER)/panda -f $(HELM_FOLDER)/panda/values.yaml -f $(HELM_FOLDER)/panda/values/values-lsst.yaml  -f $(HELM_FOLDER)/panda/values/values-use-secret.yaml > panda.yaml

harvester:
	helm template $(RELEASE_NAME_PREFIX)-harvester $(HELM_FOLDER)/harvester -f $(HELM_FOLDER)/harvester/values.yaml -f $(HELM_FOLDER)/harvester/values/values-lsst.yaml  -f $(HELM_FOLDER)/harvester/values/values-use-secret.yaml> harvester.yaml

bigmon:
	helm template $(RELEASE_NAME_PREFIX)-bigmon $(HELM_FOLDER)/bigmon -f $(HELM_FOLDER)/harvester/values.yaml > bigmon.yaml

helm: activemq iam idds panda harvester bigmon

apply:
	kubectl apply -k .

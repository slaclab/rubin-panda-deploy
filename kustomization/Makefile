RELEASE_NAME ?= dev

activemq:
	helm template activemq-$(RELEASE_NAME) ../helm/msgsvc -f ../helm/msgsvc/values.yaml -f ../helm/msgsvc/values/values-lsst.yaml -f ../helm/msgsvc/values/values-use-secret.yaml > activemq.yaml

iam:
	helm template iam-$(RELEASE_NAME) ../helm/iam -f ../helm/iam/values.yaml -f ../helm/iam/values/values-lsst.yaml -f ../helm/iam/values/values-use-secret.yaml > iam.yaml

idds:
	# helm template idds-$(RELEASE_NAME) ../helm/idds -f ../helm/idds/values.yaml -f ../helm/idds/values-lsst.yaml -f ../helm/idds/values-secret.yaml > idds.yaml
	helm template idds-$(RELEASE_NAME) ../helm/idds -f ../helm/idds/values.yaml -f ../helm/idds/values/values-lsst.yaml -f ../helm/idds/values/values-use-secret.yaml > idds.yaml

panda:
	# helm template panda-$(RELEASE_NAME) ../helm/panda -f ../helm/panda/values.yaml -f ../helm/panda/values-lsst.yaml -f ../helm/panda/values-secret.yaml> panda.yaml
	helm template panda-$(RELEASE_NAME) ../helm/panda -f ../helm/panda/values.yaml -f ../helm/panda/values/values-lsst.yaml  -f ../helm/panda/values/values-use-secret.yaml> panda.yaml

harvester:
	helm template harvester-$(RELEASE_NAME) ../helm/harvester -f ../helm/harvester/values.yaml -f ../helm/harvester/values/values-lsst.yaml  -f ../helm/harvester/values/values-use-secret.yaml> harvester.yaml

bigmon:
	helm template bigmon-$(RELEASE_NAME) ../helm/bigmon -f ../helm/harvester/values.yaml > bigmon.yaml

helm: activemq iam idds panda harvester bigmon

apply:
	kubectl apply -k .

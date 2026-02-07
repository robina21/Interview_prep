
Redshift spectrum external tables creation need a glue db. It doesnt have to be existing you can just add a new name to the create external schema query and it shoudl work.

CREATE EXTERNAL SCHEMA spectrum_ehr_claims_2026_02_03
FROM DATA CATALOG
DATABASE 'ehr_claims_db'   
IAM_ROLE 'arn:aws:iam::000000043252:role/redshiftrole'  

CREATE EXTERNAL TABLE "spectrum_ehr_claims_2026_02_03"."Condition" (
    "AbatementDateTime" TIMESTAMP,
    "BodySiteMapId" BIGINT,
    "CategoryConceptId" INT,
    "ClinicalStatusConceptId" INT,
    "CodeConceptMapId" BIGINT,
    "EncounterId" VARCHAR(65535),
    "Id" VARCHAR(65535),
    "OnsetDateTime" TIMESTAMP,
    "PatientId" VARCHAR(65535),
    "PersonId" VARCHAR(65535),
    "PrimaryDiagnosisConceptId" INT,
    "RecordedDateTime" TIMESTAMP,
    "SequenceNumber" SMALLINT,
    "SeverityConceptId" INT,
    "SourceProvenanceConceptId" INT,
    "SourceRecordId" VARCHAR(65535),
    "VerificationStatusConceptId" INT
)
STORED AS PARQUET
LOCATION 's3://bucketname/dataloadfolder/Condition/'
TABLE PROPERTIES ('parquet.compress'='SNAPPY');



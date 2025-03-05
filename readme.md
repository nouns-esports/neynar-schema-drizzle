```ts
import {
	pgTable,
	bigint,
	timestamp,
	text,
	varchar,
	jsonb,
	customType,
	smallint,
} from "drizzle-orm/pg-core";

const bytea = customType<{
	data: Buffer;
	default: false;
}>({
	dataType() {
		return "bytea";
	},
});

// https://docs.dune.com/data-catalog/community/farcaster/casts
export const dataset_farcaster_casts = pgTable("dataset_farcaster_casts", {
	id: bigint({ mode: "bigint" }).primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	deleted_at: timestamp(),
	timestamp: timestamp(),
	fid: bigint({ mode: "bigint" }),
	hash: bytea(),
	parent_hash: bytea(),
	parent_fid: bigint({ mode: "bigint" }),
	parent_url: varchar(),
	text: text(),
	embeds: jsonb(),
	mentions: bigint({ mode: "bigint" }).array(),
	mentions_positions: bigint({ mode: "bigint" }).array(),
	root_parent_hash: bytea(),
});

// https://docs.dune.com/data-catalog/community/farcaster/fids
export const dataset_farcaster_fids = pgTable("dataset_farcaster_fids", {
	fid: bigint({ mode: "bigint" }).primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	custody_address: bytea(),
});

// https://docs.dune.com/data-catalog/community/farcaster/fnames
export const dataset_farcaster_fnames = pgTable("dataset_farcaster_fnames", {
	fname: varchar().primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	deleted_at: timestamp(),
	timestamp: timestamp(),
	fid: bigint({ mode: "bigint" }),
	custody_address: bytea(),
	expires_at: timestamp(),
});

// https://docs.dune.com/data-catalog/community/farcaster/links
export const dataset_farcaster_links = pgTable("dataset_farcaster_links", {
	id: bigint({ mode: "bigint" }).primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	deleted_at: timestamp(),
	timestamp: timestamp(),
	fid: bigint({ mode: "bigint" }),
	target_fid: bigint({ mode: "bigint" }),
	hash: bytea(),
	type: text(),
});

// https://docs.dune.com/data-catalog/community/farcaster/reactions
export const dataset_farcaster_reactions = pgTable(
	"dataset_farcaster_reactions",
	{
		id: bigint({ mode: "bigint" }).primaryKey(),
		created_at: timestamp(),
		updated_at: timestamp(),
		deleted_at: timestamp(),
		timestamp: timestamp(),
		fid: bigint({ mode: "bigint" }),
		reaction_type: smallint(),
		hash: bytea(),
		target_hash: bytea(),
		target_fid: bigint({ mode: "bigint" }),
		target_url: text(),
	},
);

// https://docs.dune.com/data-catalog/community/farcaster/signers
export const dataset_farcaster_signers = pgTable("dataset_farcaster_signers", {
	id: bigint({ mode: "bigint" }).primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	deleted_at: timestamp(),
	timestamp: timestamp(),
	fid: bigint({ mode: "bigint" }),
	hash: bytea(),
	signer: bytea(),
});

// https://docs.dune.com/data-catalog/community/farcaster/storage
export const dataset_farcaster_storage = pgTable("dataset_farcaster_storage", {
	id: bigint({ mode: "bigint" }).primaryKey(),
	created_at: timestamp(),
	updated_at: timestamp(),
	deleted_at: timestamp(),
	timestamp: timestamp(),
	fid: bigint({ mode: "bigint" }),
	units: bigint({ mode: "bigint" }),
	expiry: timestamp(),
});

// https://docs.dune.com/data-catalog/community/farcaster/user_data
export const dataset_farcaster_user_data = pgTable(
	"dataset_farcaster_user_data",
	{
		id: bigint({ mode: "bigint" }).primaryKey(),
		created_at: timestamp(),
		updated_at: timestamp(),
		deleted_at: timestamp(),
		timestamp: timestamp(),
		fid: bigint({ mode: "bigint" }),
		hash: bytea(),
		type: smallint(),
	},
);

// https://docs.dune.com/data-catalog/community/farcaster/verifications
export const dataset_farcaster_verifications = pgTable(
	"dataset_farcaster_verifications",
	{
		id: bigint({ mode: "bigint" }).primaryKey(),
		created_at: timestamp(),
		updated_at: timestamp(),
		deleted_at: timestamp(),
		timestamp: timestamp(),
		fid: bigint({ mode: "bigint" }),
		hash: bytea(),
		claim: jsonb(),
	},
);

// https://docs.dune.com/data-catalog/community/farcaster/profile_with_addresses
export const dataset_farcaster_profile_with_addresses = pgTable(
	"dataset_farcaster_profile_with_addresses",
	{
		fid: bigint({ mode: "bigint" }).primaryKey(),
		fname: text(),
		display_name: text(),
		avatar_url: text(),
		bio: text(),
		verified_addresses: jsonb(),
	},
);
```